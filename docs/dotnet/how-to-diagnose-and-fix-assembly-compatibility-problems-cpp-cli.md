---
title: "如何： 診斷和修正組件相容性問題 (C + + /CLI) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- versioning, diagnosing conflicts
- versioning
- exceptions, diagnosing odd behavior
- compatibility, between assemblies
ms.assetid: 297c71e3-04a8-4d24-a5dc-b04a2c5cc6fb
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a175705bd5d303187a11bf3e7779669a3a30e483
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-diagnose-and-fix-assembly-compatibility-problems-ccli"></a>如何：診斷和修正組件相容性問題 (C++/CLI)
本主題說明在編譯時期參考的組件的版本不符合在執行階段，參考的組件版本時，會發生什麼情況以及如何避免發生問題。  
  
 當編譯組件時，可能會使用參考其他組件`#using`語法。 在編譯期間，這些組件是由編譯器所存取。 這些組件中的資訊用於達到最佳化決策。  
  
 不過，如果參考的組件會變更並重新編譯，且您未重新編譯參考的組件相依於它的這些組件可能不相容。 在有效的最佳化決策第一次可能不是正確的新組件版本。 各種執行階段錯誤可能是因為這些不相容狀況。 沒有在此情況下將不會產生任何特定例外狀況。 會發出失敗報告在執行階段的方式取決於程式碼變更造成問題的性質。  
  
 這些錯誤不應該在最後的實際執行程式碼中的問題，只要針對您的產品的發行版本重建整個應用程式。 應該使用正式的版本號碼，如此可確保這些問題得以避免標記的公開發行的組件。 如需詳細資訊，請參閱[組件版本控制](/dotnet/framework/app-domains/assembly-versioning)。  
  
### <a name="diagnosing-and-fixing-an-incompatibility-error"></a>診斷和修復不相容錯誤  
  
1.  如果您遇到執行階段例外狀況或參考另一個組件，程式碼中發生的其他錯誤狀況，而且找不到問題起因，可能會處理過期的組件。  
  
2.  首先，找出並重現或其他錯誤狀況的例外狀況。 應該可以重現因過時的例外狀況，就會發生的問題。  
  
3.  請檢查您的應用程式中參考的任何組件的時間戳記。  
  
4.  如果時間戳記，任何參考組件的應用程式的最後一個編譯時間戳記比更新版本，您的應用程式已過期。 如果發生這種情況，重新編譯應用程式與最新的組件，並進行所需的任何程式碼變更。  
  
5.  重新執行應用程式中，執行步驟重現問題，並確認不會發生例外狀況。  
  
## <a name="example"></a>範例  
 下列的程式說明問題減少的一種方法，存取範圍，並嘗試存取另一個組件中的該方法不需要重新編譯。 請嘗試編譯`changeaccess.cpp`第一次。 這是會變更參考的組件。 然後編譯`referencing.cpp`。 編譯會成功。 現在，降低呼叫方法的協助工具。 重新編譯`changeaccess.cpp`旗標`/DCHANGE_ACCESS`。 這會讓方法受到保護，而非私用，因此您可以再呼叫合法。 不需要重新編譯`referencing.exe`，重新執行應用程式。 例外狀況<xref:System.MethodAccessException>會產生。  
  
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
  
## <a name="see-also"></a>請參閱  
 [#using 指示詞](../preprocessor/hash-using-directive-cpp.md)   
 [Managed 類型 (C++/CLI)](../dotnet/managed-types-cpp-cli.md)