---
title: "safe_cast （c + + 元件擴充功能） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- safe_cast
- safe_cast_cpp
- stdcli::language::safe_cast
dev_langs:
- C++
helpviewer_keywords:
- safe_cast keyword [C++]
ms.assetid: 4fa688bf-a8ec-49bc-a4c5-f48134efa4f7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 14bcf198d527fae51a579a2aa6e072a4c57424f1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="safecast-c-component-extensions"></a>safe_cast (C++ 元件擴充功能)
如果成功，`safe_cast` 作業會傳回指定的運算式做為指定的類型，否則會擲回 `InvalidCastException`。  
  
## <a name="all-runtimes"></a>所有執行階段  
 (這個語言功能沒有適用所有執行階段的備註。)  
  
### <a name="syntax"></a>語法  
  
```cpp  
[default]:: safe_cast<  
type-id  
>(  
expression  
)  
  
```  
  
### <a name="parameters"></a>參數  
  
### <a name="remarks"></a>備註  
  
## <a name="windows-runtime"></a>Windows 執行階段  
 `safe_cast` 可讓您變更指定運算式的類型。 在您完全預期變數或參數可轉換成特定類型的情況下，您可以使用 safe_cast 而不需使用 try-catch 區塊，即可在開發期間偵測程式設計錯誤。 如需詳細資訊，請參閱[轉型 (C + + /CX)](http://msdn.microsoft.com/library/windows/apps/hh755802.aspx)。  
  
### <a name="syntax"></a>語法  
  
```cpp  
[default]:: safe_cast<  
type-id  
>(  
expression  
)  
  
```  
  
### <a name="parameters"></a>參數  
 *類型識別碼*  
 要轉換的類型*運算式*至。 一個控制代碼，可用來參考或值類型、值類型，或參考或值類型的追蹤參考。  
  
 *運算式*  
 一個運算式，可針對用來參考或值類型、值類型，或參考或值類型的追蹤參考之控制代碼進行評估。  
  
### <a name="remarks"></a>備註  
 `safe_cast`擲回`InvalidCastException`如果它無法轉換*運算式*所指定的型別*類型識別碼*。若要攔截`InvalidCastException`，指定[/EH （例外狀況處理模型）](../build/reference/eh-exception-handling-model.md)編譯器選項，並使用 try/catch 陳述式。  
  
### <a name="requirements"></a>需求  
 編譯器選項： **/ZW**  
  
### <a name="examples"></a>範例  
 **範例**  
  
 下列程式碼範例示範如何使用`safe_cast`與 Windows 執行階段。  
  
```cpp#  
// safe_cast_ZW.cpp  
// compile with: /ZW /EHsc  
  
using namespace default;  
using namespace Platform;  
  
interface class I1 {};  
interface class I2 {};  
interface class I3 {};  
  
ref class X : public I1, public I2 {};  
  
int main(Array<String^>^ args) {  
   I1^ i1 = ref new X;  
   I2^ i2 = safe_cast<I2^>(i1);   // OK, I1 and I2 have common type: X  
   // I2^ i3 = static_cast<I2^>(i1);   C2440 use safe_cast instead  
   try {  
      I3^ i4 = safe_cast<I3^>(i1);   // Fails because i1 is not derived from I3.  
   }   
   catch(InvalidCastException^ ic) {  
     wprintf(L"Caught expected exception: %s\n", ic->Message);  
   }  
}  
```  
  
 **輸出**  
  
```Output  
Caught expected exception: InvalidCastException  
```  
  
## <a name="common-language-runtime"></a>Common Language Runtime 
 `safe_cast` 可讓您變更運算式的類型，並產生可驗證的 MSIL 程式碼。  
  
### <a name="syntax"></a>語法  
  
```cpp  
[cli]:: safe_cast<  
type-id  
>(  
expression  
)  
  
```  
  
### <a name="parameters"></a>參數  
 *類型識別碼*  
 一個控制代碼，可用來參考或值類型、值類型，或參考或值類型的追蹤參考。  
  
 *運算式*  
 一個運算式，可針對用來參考或值類型、值類型，或參考或值類型的追蹤參考之控制代碼進行評估。  
  
### <a name="remarks"></a>備註  
 運算式`safe_cast<`*類型識別碼*`>(`*運算式*`)`將運算元運算式轉換成 type-id 類型的物件。  
  
 編譯器會接受[static_cast](../cpp/static-cast-operator.md)在大多數的地方，就會接受`safe_cast`。  不過，`safe_cast` 保證能夠產生可驗證的 MSIL，其中的 `static_cast` 可能會產生無法驗證的 MSIL。  請參閱[純粹的和可驗證程式碼 (C + + /CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)和[Peverify.exe （PEVerify 工具）](/dotnet/framework/tools/peverify-exe-peverify-tool)如需有關驗證的程式碼。  
  
 如同 `static_cast`，`safe_cast` 會叫用使用者定義的轉換。  
  
 如需有關轉換的詳細資訊，請參閱[轉型運算子](../cpp/casting-operators.md)。  
  
 `safe_cast`不會套用**const_cast** (沒有**const**)。  
  
 `safe_cast` 位於 cli 命名空間。  請參閱[平台、 default 和 cli 命名空間](../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md)如需詳細資訊。  
  
 如需有關**safe_cas**t，請參閱：  
  
-   [使用 /clr 進行 C-style 轉換 (C + + /CLI)](../windows/c-style-casts-with-clr-cpp-cli.md)  
  
-   [如何：在 C++/CLI 中使用 safe_cast](../dotnet/how-to-use-safe-cast-in-cpp-cli.md)  

### <a name="requirements"></a>需求  
 編譯器選項： **/clr**  
  
### <a name="examples"></a>範例  
 **範例**  
  
 一個適用於不相關的介面類型之間轉型的範例，其中編譯器不會接受 `static_cast` 但接受 `safe_cast`。  使用 `safe_cast` 時，編譯器不會發出轉換錯誤，並會在執行階段上執行檢查以查看是否能轉型  
  
```cpp  
// safe_cast.cpp  
// compile with: /clr  
using namespace System;  
  
interface class I1 {};  
interface class I2 {};  
interface class I3 {};  
  
ref class X : public I1, public I2 {};  
  
int main() {  
   I1^ i1 = gcnew X;  
   I2^ i2 = safe_cast<I2^>(i1);   // OK, I1 and I2 have common type: X  
   // I2^ i3 = static_cast<I2^>(i1);   C2440 use safe_cast instead  
   try {  
      I3^ i4 = safe_cast<I3^>(i1);   // fail at runtime, no common type  
   }   
   catch(InvalidCastException^) {  
      Console::WriteLine("Caught expected exception");  
   }  
}  
```  
  
 **輸出**  
  
```Output  
Caught expected exception  
```  
  
## <a name="see-also"></a>請參閱  
 [執行階段平台的元件延伸模組](../windows/component-extensions-for-runtime-platforms.md)