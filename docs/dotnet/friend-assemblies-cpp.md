---
title: "Friend 組件 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Friend 組件，Visual C++"
ms.assetid: 8d55fee0-b7c2-4fbe-a23b-dfe424dc71cd
caps.latest.revision: 27
caps.handback.revision: 27
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Friend 組件 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

適用的執行階段， *friend 組件* 組譯碼語言功能在命名空間範圍或全域範圍在組件元件可供一個或多個用戶端組件或 .netmodule 的型別。  
  
## 所有執行階段  
 **備註**  
  
 \(這個語言功能不會在所有執行階段中支援。\)  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
 **備註**  
  
 \(在[!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]中不支援此語言功能。\)  
  
### 需求  
 編譯器選項：**\/ZW**  
  
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
 **備註**  
  
#### 將型別會在命名空間範圍或全域範圍在組件元件可存取的到用戶端組件或 .netmodule  
  
1.  在元件，請指定組件屬性 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>，並將存取型別會在命名空間範圍或全域範圍在元件用戶端組件或 .netmodule 的名稱。您可以指定其他屬性指定多個用戶端組件或 .netmodule。  
  
2.  在這個用戶端組件或 .netmodule，使用 `#using`時，也就是說，當您參考元件組件，請將 `as_friend` 屬性。如果您未指定 `InternalsVisibleToAttribute`的組件指定 `as_friend` 屬性，執行階段會擲回例外狀況，如果您嘗試存取型別會在命名空間範圍或全域範圍在元件。  
  
 建置錯誤會發生，則包含 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性的組件沒有強式名稱，而是組件使用 `as_friend` 屬性的用戶端。  
  
 雖然在命名空間範圍和全域範圍的型別可以為用戶端組件或 .netmodule 所知，成員存取範圍仍然有效。例如，您無法存取私用成員。  
  
 必須明確授與所有型別的輸入組件中。例如，組件 C 無法存取任何型別的組件中的，如果組件 C 參考 B 組件，而組件 B 可以存取所有型別在組件 A。  
  
 如需如何指定型別的存取範圍的詳細資訊可以在組件之外\)，請參閱 [類型可視性](../misc/type-visibility.md)。  
  
 如需標記是使用 Visual C\+\+ 編譯器，如何對所建置組件的強式名稱方式的詳細資訊請參閱 [強式名稱組件 \(組件簽署\)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)。  
  
 對使用 friend 組件功能，您的方法可以使用 <xref:System.Security.Permissions.StrongNameIdentityPermission> 限制對個別型別存取。  
  
### 需求  
 編譯器選項：**\/clr**  
  
### 範例  
 下列程式碼範例會定義指定用戶端組件存取型別在元件的元件。  
  
```  
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
  
 下一個程式碼範例會存取在元件的私用型別。  
  
```  
// friend_assemblies_2.cpp  
// compile by using: /clr  
#using "friend_assemblies.dll" as_friend  
  
int main() {  
   Class1 ^ a = gcnew Class1;  
   a->Test_Public();  
}  
```  
  
 **Output**  
  
 `Class1::Test_Public`  
  
 下一個程式碼範例會定義元件，但不指定將可以存取型別的元件中的用戶端組件。  
  
 請使用 **\/opt:noref**元件連接。  這可確保私用型別在元件的中繼資料中發出，當 `InternalsVisibleTo` 屬性存在時不需要。  如需詳細資訊，請參閱[\/OPT \(最佳化\)](../build/reference/opt-optimizations.md)。  
  
```  
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
  
 下列程式碼範例會定義嘗試存取在元件的私用型別不允許對其私用型別的可存取的用戶端。  由於執行階段的行為，因此，如果您要攔截例外狀況，您必須嘗試存取在 Helper 函式的私用型別。  
  
```  
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
  
 **Output**  
  
 `caught an exception`  
  
 下一個程式碼範例顯示如何建立指定用戶端組件可以存取型別的元件上的強式名稱元件。  
  
```  
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
  
 請注意元件必須指定公開金鑰。  建議您依序執行下列命令在命令提示字元建立金鑰組並取得公開金鑰:  
  
 **sn \-d friend\_assemblies.snk**  
  
 **sn \-k friend\_assemblies.snk**  
  
 **sn \-i friend\_assemblies.snk friend\_assemblies.snk**  
  
 **sn \-pc friend\_assemblies.snk key.publickey**  
  
 **sn \-tp key.publickey**  
  
 下一個程式碼範例會存取在強式名稱元件的私用型別。  
  
```  
// friend_assemblies_6.cpp  
// compile by using: /clr /link /keyfile:friend_assemblies.snk  
#using "friend_assemblies_5.dll" as_friend  
  
int main() {  
   Class1 ^ a = gcnew Class1;  
   a->Test_Public();  
}  
```  
  
 **Output**  
  
 `Class1::Test_Public`  
  
## 請參閱  
 [Component Extensions for Runtime Platforms](../windows/component-extensions-for-runtime-platforms.md)