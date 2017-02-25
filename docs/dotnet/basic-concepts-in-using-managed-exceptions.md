---
title: "使用 Managed 例外狀況中的基本概念 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__finally 關鍵字, Managed 例外狀況"
  - "catch 區塊"
  - "例外狀況, Managed"
  - "擲回例外狀況, Managed 例外狀況"
  - "try-catch 例外狀況處理"
  - "try-catch 例外狀況處理, Managed 應用程式"
  - "Visual C++, 處理 Managed 例外狀況"
ms.assetid: 40ce8931-1ecc-491a-815f-733b23fcba35
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# 使用 Managed 例外狀況中的基本概念
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這個主題討論在 Managed 應用程式中處理例外狀況。  也就是與 **\/clr** 編譯器選項編譯的應用程式。  
  
## 本主題內容  
  
-   [在 \/clr 下擲回的例外狀況](#vcconbasicconceptsinusingmanagedexceptionsanchor1)  
  
-   [CLR 副檔名的 try\/catch 區塊](#vcconbasicconceptsinusingmanagedexceptionsanchor2)  
  
## 備註  
 如果您與 **\/clr** 選項編譯，您可以處理 CLR 例外狀況以及標準的 [C\+\+ 例外狀況處理](../cpp/cpp-exception-handling.md) 和 [結構化例外處理](../cpp/structured-exception-handling-c-cpp.md) \(SEH\)。  CLR 例外狀況是 Managed 型別會擲回的任何例外狀況。  [System::Exception](https://msdn.microsoft.com/en-us/library/system.exception.aspx) 類別提供許多處理 CLR 例外狀況的有用方法，並且建議做為使用者定義的例外狀況類別的基底類別。  
  
 攔截衍生自介面的例外狀況型別並不在 **\/clr** 下被支援。  此外， Common Language Runtime 不允許您攔截堆疊溢位例外狀況；堆疊溢位例外狀況會結束處理序。  
  
 如需在 Managed 和 Unmanaged 應用程式處理例外狀況的差異之詳細資訊，請參閱 [C\+\+ 中 Managed Extensions 的例外狀況處理行為之差異](../dotnet/differences-in-exception-handling-behavior-under-clr.md)。  
  
##  <a name="vcconbasicconceptsinusingmanagedexceptionsanchor1"></a> 在 \/clr 下擲回的例外狀況  
 C\+\+ 擲回運算式已擴充為擲回控制代碼至 CLR 型別。  下列範例會建立自訂例外狀況型別，然後擲回該型別的執行個體：  
  
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
  
 必須在擲回之前 Boxed 的實值型別：  
  
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
  
##  <a name="vcconbasicconceptsinusingmanagedexceptionsanchor2"></a> CLR 副檔名的 try\/catch 區塊  
 同一個 **try**\/**catch** 區塊結構可用於攔截 CLR 和原生例外狀況：  
  
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
  
### Output  
  
```  
In 'catch(CMyClass& catchC)'  
2  
In 'catch(MyStruct^ catchException)'  
11  
```  
  
### 順序回溯的 C\+\+ 物件  
 附有解構函式的任何 C\+\+ 物件都可能發生回溯，可能是在擲回函式和處理函式之間的執行階段堆疊上。  由於 CLR 型別配置在堆積上，回溯不適用於它們。  
  
 已擲回例外狀況的事件順序如下：  
  
1.  執行階段在堆疊中尋找適當的 catch 子句，或者在 SEH 的情況下，是尋找 SEH 的篩選條件，以攔截例外狀況。  按語彙順序會先搜尋 catch 子句，然後動態地在呼叫堆疊中繼續尋找。  
  
2.  一旦找到正確的處理常式，堆疊會回溯至該點。  對於堆疊上的每個函式呼叫，它的區域物件會被解構，並且巢狀的向外執行 \_\_finally 區塊。  
  
3.  一旦堆疊回溯時， catch 子句執行。  
  
### 攔截 Unmanaged 型別  
 當 Unmanaged 物件型別擲回時，它會與 [System::Runtime.InteropServices::SEHException](https://msdn.microsoft.com/en-us/library/system.runtime.interopservices.sehexception.aspx) 型別的例外狀況一起包裝。  搜尋適當的 **catch** 子句時，有兩種可能性。  
  
-   如果遇到原生 C\+\+ 型別，例外狀況會解除包裝並與遇到的型別比較。  這比較允許原生 C\+\+ 型別以一般方式被攔截。  
  
-   不過，如果型別 **SEHException** 的 **catch** 子句首先被檢查，子句會攔截例外狀況。  因此，您應該將所有先攔截 C\+\+ 型別的 catch 子句放置在任何 CLR 型別的 catch 子句之前。  
  
 請注意  
  
```  
catch(Object^)  
```  
  
 和  
  
```  
catch(...)  
```  
  
 兩者會攔截包括 SEH 例外狀況的任何擲回型別。  
  
 如果一個 Unmanaged 型別由 catch \(Object^\) 攔截，它不會終結被擲回的物件。  
  
 當擲回或攔截 Unmanaged 例外狀況時，我們建議您使用 [\/EHsc](../build/reference/eh-exception-handling-model.md) 編譯器選項，而不是 **\/EHs** 或 **\/EHa**。  
  
## 請參閱  
 [Exception Handling](../windows/exception-handling-cpp-component-extensions.md)   
 [safe\_cast](../windows/safe-cast-cpp-component-extensions.md)   
 [例外狀況處理](../cpp/exception-handling-in-visual-cpp.md)