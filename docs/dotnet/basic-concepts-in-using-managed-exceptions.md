---
title: Managed 例外狀況中使用的基本概念 |Microsoft 文件
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
- try-catch exception handling, managed applications
- __finally keyword, managed exceptions
- exceptions, managed
- try-catch exception handling
- catch blocks
- throwing exceptions, managed exceptions
- Visual C++, handling managed exceptions
ms.assetid: 40ce8931-1ecc-491a-815f-733b23fcba35
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 5e2faf56f050610e6c98ff82cdca10333a54fd93
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="basic-concepts-in-using-managed-exceptions"></a>使用 Managed 例外狀況中的基本概念
本主題討論在 managed 應用程式中處理的例外狀況。 也就是使用編譯的應用程式**/clr**編譯器選項。  
  
## <a name="in-this-topic"></a>本主題內容  
  
-   [擲回的 /clr 之下例外狀況](#vcconbasicconceptsinusingmanagedexceptionsanchor1)  
  
-   [Try/Catch 區塊 CLR 延伸模組](#vcconbasicconceptsinusingmanagedexceptionsanchor2)  
  
## <a name="remarks"></a>備註  
 如果您使用編譯**/clr**選項，您可以處理 CLR 例外狀況，以及標準[c + + 例外狀況處理](../cpp/cpp-exception-handling.md)和[結構化例外狀況處理](../cpp/structured-exception-handling-c-cpp.md)(SEH)。 CLR 例外狀況是 managed 型別所擲回任何例外狀況。 [System:: exception](https://msdn.microsoft.com/en-us/library/system.exception.aspx)類別提供許多有用的方法，以處理 CLR 例外狀況，並建議使用者定義的例外狀況類別的基底類別。  
  
 攔截例外狀況類型衍生自介面不支援**/clr**。 此外，common language runtime 不允許您攔截堆疊溢位例外狀況。堆疊溢位例外狀況會終止處理程序。  
  
 如需在 managed 和 unmanaged 應用程式中的例外狀況處理差異的詳細資訊，請參閱[例外狀況處理行為在 Managed Extensions for c + + 中的差異](../dotnet/differences-in-exception-handling-behavior-under-clr.md)。  
  
##  <a name="vcconbasicconceptsinusingmanagedexceptionsanchor1"></a>擲回的 /clr 之下例外狀況  
 C + + throw 運算式會延伸至 CLR 型別擲回的控制代碼。 下列範例會建立自訂例外狀況型別，然後擲回該類型的執行個體：  
  
```  
// clr_exception_handling.cpp  
// compile with: /clr /c  
ref struct MyStruct: public System::Exception {  
public:  
   int i;  
};  
  
void GlobalFunction() {  
   MyStruct^ pMyStruct = gcnew MyStruct;  
   throw pMyStruct;  
}  
```  
  
 實值類型必須進行 boxed 處理之前擲回：  
  
```  
// clr_exception_handling_2.cpp  
// compile with: /clr /c  
value struct MyValueStruct {  
   int i;  
};  
  
void GlobalFunction() {  
   MyValueStruct v = {11};  
   throw (MyValueStruct ^)v;  
}  
```  
  
##  <a name="vcconbasicconceptsinusingmanagedexceptionsanchor2"></a>Try/Catch 區塊 CLR 延伸模組  
 相同**再試一次**/**攔截**區塊結構可用來擷取 CLR 和原生例外狀況：  
  
```  
// clr_exception_handling_3.cpp  
// compile with: /clr  
using namespace System;  
ref struct MyStruct : public Exception {  
public:  
   int i;  
};  
  
struct CMyClass {  
public:  
   double d;  
};  
  
void GlobalFunction() {  
   MyStruct^ pMyStruct = gcnew MyStruct;  
   pMyStruct->i = 11;  
   throw pMyStruct;  
}  
  
void GlobalFunction2() {  
   CMyClass c = {2.0};  
   throw c;  
}  
  
int main() {  
   for ( int i = 1; i >= 0; --i ) {  
      try {  
         if ( i == 1 )  
            GlobalFunction2();  
         if ( i == 0 )  
            GlobalFunction();  
      }  
      catch ( CMyClass& catchC ) {  
         Console::WriteLine( "In 'catch(CMyClass& catchC)'" );  
         Console::WriteLine( catchC.d );  
      }  
      catch ( MyStruct^ catchException ) {  
         Console::WriteLine( "In 'catch(MyStruct^ catchException)'" );  
         Console::WriteLine( catchException->i );  
      }  
   }  
}  
```  
  
### <a name="output"></a>輸出  
  
```  
In 'catch(CMyClass& catchC)'  
2  
In 'catch(MyStruct^ catchException)'  
11  
```  
  
### <a name="order-of-unwinding-for-c-objects"></a>回溯 c + + 物件的順序  
 回溯會發生在具有解構函式可能擲回的函式與處理函式之間，執行階段堆疊上之任何 c + + 物件。 因為 CLR 型別會配置在堆積上，回溯不適用於它們。  
  
 擲回的例外狀況的事件順序如下所示：  
  
1.  執行階段查核堆疊尋找適當的 catch 子句，或在 SEH，除了 SEH，來攔截例外狀況篩選條件。 Catch 子句會先搜尋語彙順序，然後動態地向下呼叫堆疊。  
  
2.  一旦找到正確的處理常式，則堆疊會回溯至該點。 每個函式呼叫堆疊上，其本機物件解構和 __finally 區塊會執行結果，從最外巢狀。  
  
3.  一旦回溯堆疊時，會執行的 catch 子句。  
  
### <a name="catching-unmanaged-types"></a>攔截的 Unmanaged 的類型  
 擲回的未受管理的物件類型時，它會包裝的例外狀況型別的[System::Runtime.InteropServices::SEHException](https://msdn.microsoft.com/en-us/library/system.runtime.interopservices.sehexception.aspx)。 搜尋適當時**攔截**子句中，有兩種可能性。  
  
-   如果遇到原生 c + + 類型時，例外狀況會解除包裝，且相較於遇到的型別。 這項比較可讓您以正常方式攔截原生 c + + 類型。  
  
-   不過，如果**攔截**型別的子句**SEHException**或其任何基底類別的第一次會進行檢查，子句會攔截的例外狀況。 因此，您應該將任何攔截的 CLR 型別子句之前，先攔截原生 c + + 類型的所有 catch 子句。  
  
 請注意：  
  
```  
catch(Object^)  
```  
  
 和  
  
```  
catch(...)  
```  
  
 將會同時攔截任何擲回的型別，包括 SEH 例外狀況。  
  
 如果 catch(Object^) 被攔截的 unmanaged 的類型，它並不會終結擲回的物件。  
  
 當擲回或攔截 unmanaged 例外狀況時，我們建議您使用[/EHsc](../build/reference/eh-exception-handling-model.md)編譯器選項，而非**/EHs**或**/EHa**。  
  
## <a name="see-also"></a>請參閱  
 [例外狀況處理](../windows/exception-handling-cpp-component-extensions.md)   
 [safe_cast](../windows/safe-cast-cpp-component-extensions.md)   
 [例外狀況處理](../cpp/exception-handling-in-visual-cpp.md)