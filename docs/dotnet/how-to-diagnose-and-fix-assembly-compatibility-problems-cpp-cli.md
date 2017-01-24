---
title: "如何：診斷和修正組件相容性問題 (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "相容性, 組件之間"
  - "例外狀況, 診斷異常行為"
  - "版本控制"
  - "版本控制, 診斷衝突"
ms.assetid: 297c71e3-04a8-4d24-a5dc-b04a2c5cc6fb
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：診斷和修正組件相容性問題 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主題說明當編譯時期所參考的組件版本與執行階段所參考的組件版本不相符時，會發生什麼事以及如何避免這個問題。  
  
 編譯某個組件時，可能也正透過 `#using` 語法參考其他組件。  在編譯期間，編譯器會存取這些組件。  這些組件中的資訊可以用來達到最佳化決策。  
  
 但是，如果已變更並重新編譯參考的組件，但是並未重新編譯具有相依關係的引用組件，這些組件可能就不相容。  一開始有效的最佳化決策在新組件版本中卻不一定正確。  這些不相容的情況可能會造成各種執行階段錯誤。  在這類情況下並沒有特定的例外狀況。  在執行階段報告錯誤的方式，需視引起錯誤之程式碼變更的本質而定。  
  
 一旦針對產品的發行版本重新建置整個應用程式之後，這些錯誤就不應該在最終的正式程式碼中出現。  公開發行的組件會標示正式的版本號碼，這也表示已去除這些問題。  如需詳細資訊，請參閱[組件版本控制](../Topic/Assembly%20Versioning.md)。  
  
### 診斷和修正不相容問題  
  
1.  如果您在參考另一個組件的程式碼中遇到執行階段例外狀況或發生其他錯誤情況，而且找不到問題起因，那麼可能是您使用的組件已過期。  
  
2.  首先，隔離並重現例外狀況或其他錯誤情況。  您應該可以重現因過期例外狀況所導致的問題。  
  
3.  檢查在您的應用程式中所參考之任何組件的時間戳記。  
  
4.  如果任何參考之組件的時間戳記比應用程式最後一次編譯的時間戳記還晚，就表示應用程式已經過期。  如果發生這種情況，請以最新的組件重新編譯應用程式，並且進行任何必要的程式碼變更。  
  
5.  重新執行應用程式，執行會重現問題的步驟，並確認已不再發生例外狀況。  
  
## 範例  
 下列程式會減少方法的存取範圍，然後在不重新編譯的情況下，嘗試直接存取另一個組件中的方法，以說明此問題。  一開始先嘗試編譯 `changeaccess.cpp`。  這是將要進行變更之參考的組件。  接著編譯 `referencing.cpp`。  成功完成編譯。  現在，減少呼叫之方法的存取範圍。  以旗標 `/DCHANGE_ACCESS` 重新編譯 `changeaccess.cpp`。  這樣會使方法變成保護的 \(Protected\) 而非私用的 \(Private\)，因此再也無法合法地呼叫此方法。  不要重新編譯 `referencing.exe`，直接重新執行應用程式。  <xref:System.MethodAccessException> 例外狀況便會發生。  
  
```  
// changeaccess.cpp  
// compile with: /clr:safe /LD  
// After the initial compilation, add /DCHANGE_ACCESS and rerun  
// referencing.exe to introduce an error at runtime. To correct  
// the problem, recompile referencing.exe  
  
public ref class Test {  
#if defined(CHANGE_ACCESS)  
protected:  
#else  
public:  
#endif  
  
  int access_me() {  
    return 0;  
  }  
  
};  
  
```  
  
```  
// referencing.cpp  
// compile with: /clr:safe   
#using <changeaccess.dll>  
  
// Force the function to be inline, to override the compiler's own  
// algorithm.  
__forceinline  
int CallMethod(Test^ t) {  
  // The call is allowed only if access_me is declared public  
  return t->access_me();  
}  
  
int main() {  
  Test^ t = gcnew Test();  
  try  
  {  
    CallMethod(t);  
    System::Console::WriteLine("No exception.");  
  }  
  catch (System::Exception ^ e)  
  {  
    System::Console::WriteLine("Exception!");  
  }  
  return 0;  
}  
  
```  
  
## 請參閱  
 [\#using 指示詞](../preprocessor/hash-using-directive-cpp.md)   
 [Managed 類型](../dotnet/managed-types-cpp-cli.md)