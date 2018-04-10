---
title: Friend 組件 （c + +） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- friend assemblies, Visual C++
ms.assetid: 8d55fee0-b7c2-4fbe-a23b-dfe424dc71cd
caps.latest.revision: 27
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6646306092844f11819b81ee076c54db840c618b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="friend-assemblies-c"></a>Friend 組件 (C++)
適用於執行階段，如*friend 組件*語言功能可讓位於命名空間範圍或全域範圍中的一個或多個用戶端組件或.netmodule 可以存取的組件元件的類型。  
  
## <a name="all-runtimes"></a>所有執行階段  
 **備註**  
  
 (不是所有執行階段都有支援這個語言功能)。  
  
## <a name="windows-runtime"></a>Windows 執行階段  
 **備註**  
  
 （這個語言功能不支援在 Windows 執行階段）。  
  
### <a name="requirements"></a>需求  
 編譯器選項： **/ZW**  
  
## <a name="common-language-runtime"></a>Common Language Runtime 
 **備註**  
  
#### <a name="to-make-types-at-namespace-scope-or-global-scope-in-an-assembly-component-accessible-to-a-client-assembly-or-netmodule"></a>讓組件元件中在命名空間範圍或全域範圍的類型可存取用戶端組件或 .netmodule  
  
1.  在元件中，指定組件屬性 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>，並傳遞將存取元件中在命名空間範圍或全域範圍之類型的用戶端組件或 .netmodule 的名稱。  您可以藉由指定其他屬性來指定多個用戶端組件或 .netmodule。  
  
2.  在用戶端組件或 .netmodule 中，當您使用 `#using` 參考元件組件時，請傳遞 `as_friend` 屬性。  如果您為組件指定的 `as_friend` 屬性並未指定 `InternalsVisibleToAttribute`，如果您嘗試存取元件中在命名空間範圍或全域範圍的類型，將會擲回執行階段例外狀況。  
  
 如果包含 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性的組件沒有強式名稱，而是使用 `as_friend` 屬性的用戶端組件卻有強式名稱，此時會發生建置錯誤。  
  
 雖然在命名空間範圍和全域範圍的類型可以讓用戶端組件或 .netmodule 知道，成員存取範圍仍然有效。  例如，您無法存取私人成員。  
  
 必須明確授與組件中所有類型的存取權。  例如，如果組件 C 參考組件 B，而組件 B 具有組件 A 中所有類型的存取權，則組件 C 沒有組件 A 中所有類型的存取權。  
  
 如需有關如何簽署資訊 — 也就是如何提供強式名稱 — 建置組件時所使用的 Visual c + + 編譯器，請參閱[強式名稱組件 （組件簽署） (C + + CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)。  
  
 對於使用 friend 組件功能的替代方案，您可以使用 <xref:System.Security.Permissions.StrongNameIdentityPermission> 限制對個別類型的存取。  
  
### <a name="requirements"></a>需求  
 編譯器選項： **/clr**  
  
### <a name="examples"></a>範例  
 下列程式碼範例會定義可指定具有元件類型存取權之用戶端組件的元件。  
  
```cpp  
// friend_assemblies.cpp  
// compile by using: /clr /LD  
using namespace System::Runtime::CompilerServices;  
using namespace System;  
// an assembly attribute, not bound to a type  
[assembly:InternalsVisibleTo("friend_assemblies_2")];  
  
ref class Class1 {  
public:  
   void Test_Public() {  
      Console::WriteLine("Class1::Test_Public");  
   }  
};  
```  
  
 下一個程式碼範例會存取元件中的私用類型。  
  
```cpp  
// friend_assemblies_2.cpp  
// compile by using: /clr  
#using "friend_assemblies.dll" as_friend  
  
int main() {  
   Class1 ^ a = gcnew Class1;  
   a->Test_Public();  
}  
```  
  
```Output  
Class1::Test_Public  
```  
  
 下一個程式碼範例會定義元件，但不指定具有元件中各類型之存取權的用戶端組件。  
  
 請注意使用連結元件**/opt: noref**。 這可確保私用類型在元件的中繼資料中發出，當 `InternalsVisibleTo` 屬性存在時則不需要。 如需詳細資訊，請參閱[/editandcontinue （最佳化）](../build/reference/opt-optimizations.md)。  
  
```cpp  
// friend_assemblies_3.cpp  
// compile by using: /clr /LD /link /opt:noref  
using namespace System;  
  
ref class Class1 {  
public:  
   void Test_Public() {  
      Console::WriteLine("Class1::Test_Public");  
   }  
};  
```  
  
 下列程式碼範例會定義嘗試存取元件中私用類型 (其未將存取權授與其私用類型) 的用戶端。 由於執行階段的行為，如果您要攔截例外狀況，您必須嘗試存取在 helper 函式的私用類型。  
  
```cpp  
// friend_assemblies_4.cpp  
// compile by using: /clr  
#using "friend_assemblies_3.dll" as_friend  
using namespace System;  
  
void Test() {  
   Class1 ^ a = gcnew Class1;  
}  
  
int main() {  
   // to catch this kind of exception, use a helper function  
   try {  
      Test();     
   }  
   catch(MethodAccessException ^ e) {  
      Console::WriteLine("caught an exception");  
   }  
}  
```  
  
```Output  
caught an exception  
```
  
 下一個程式碼範例顯示如何建立可指定具有元件類型存取權之用戶端組件的強式名稱元件。  
  
```cpp  
// friend_assemblies_5.cpp  
// compile by using: /clr /LD /link /keyfile:friend_assemblies.snk  
using namespace System::Runtime::CompilerServices;  
using namespace System;  
// an assembly attribute, not bound to a type  
  
[assembly:InternalsVisibleTo("friend_assemblies_6, PublicKey=00240000048000009400000006020000002400005253413100040000010001000bf45d77fd991f3bff0ef51af48a12d35699e04616f27ba561195a69ebd3449c345389dc9603d65be8cd1987bc7ea48bdda35ac7d57d3d82c666b7fc1a5b79836d139ef0ac8c4e715434211660f481612771a9f7059b9b742c3d8af00e01716ed4b872e6f1be0e94863eb5745224f0deaba5b137624d7049b6f2d87fba639fc5")];  
  
private ref class Class1 {  
public:  
   void Test_Public() {  
      Console::WriteLine("Class1::Test_Public");  
   }  
};  
```  
  
 請注意，該元件必須指定其公開金鑰。 建議您依序在命令提示字元執行下列命令，以建立金鑰組，並取得公開金鑰：  
  
 **sn-d friend_assemblies.snk**  
  
 **sn-k friend_assemblies.snk**  
  
 **sn-i friend_assemblies.snk friend_assemblies.snk**  
  
 **sn-pc friend_assemblies.snk key.publickey**  
  
 **sn-tp key.publickey**  
  
 下一個程式碼範例會存取在強式名稱元件中的私用類型。  
  
```cpp  
// friend_assemblies_6.cpp  
// compile by using: /clr /link /keyfile:friend_assemblies.snk  
#using "friend_assemblies_5.dll" as_friend  
  
int main() {  
   Class1 ^ a = gcnew Class1;  
   a->Test_Public();  
}  
```  
  
```Output  
Class1::Test_Public  
```  
  
## <a name="see-also"></a>請參閱  
 [執行階段平台的元件延伸模組](../windows/component-extensions-for-runtime-platforms.md)