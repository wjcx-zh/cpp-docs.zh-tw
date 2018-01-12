---
title: "連結器工具警告 LNK4049 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4049
dev_langs: C++
helpviewer_keywords: LNK4049
ms.assetid: 5fd5fb24-c860-4149-a557-0ac26a65d97c
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f44634bd99e485e444ffe9cee7747f31374becf4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4049"></a>連結器工具警告 LNK4049
本機定義的符號 'symbol' 匯入  
  
 符號已同時從匯出和匯入程式。  
  
 當您使用宣告的符號連結器便會產生這個警告`__declspec(dllexport)`儲存類別屬性一個目的檔中，使用參考`__declspec(dllimport)`中另一個屬性。  
  
 警告 LNK4049 是更廣泛版本的[連結器工具警告 LNK4217](../../error-messages/tool-errors/linker-tools-warning-lnk4217.md)。 連結器產生警告 LNK4049 時它無法判斷哪一個函式從參考匯入的符號。  
  
 常見的情況，而不是 LNK4217 產生 LNK4049 的位置如下：  
  
-   執行使用累加連結[/增量](../../build/reference/incremental-link-incrementally.md)選項。  
  
-   使用執行整個程式最佳化[/LTCG](../../build/reference/ltcg-link-time-code-generation.md)選項。  
  
 若要解決 LNK4049，請嘗試下列其中一項：  
  
-   移除`__declspec(dllimport)`觸發 LNK4049 符號的向前宣告從宣告的名稱。 您可以搜尋符號，二進位映像內使用**DUMPBIN**公用程式。 **DUMPBIN/符號**參數顯示 COFF 符號表，映像。 如需有關**DUMPBIN**公用程式，請參閱[DUMPBIN 參考](../../build/reference/dumpbin-reference.md)。  
  
-   暫時停用累加連結和整個程式最佳化。 重新編譯應用程式將會產生警告 LNK4217，其中包含要從中匯入的符號參考的函數的名稱。 移除`__declspec(dllimport)`從匯入的符號和啟用累加連結或整個程式最佳化，視需要的宣告。  
  
 雖然最後產生的程式碼會正常運作，呼叫匯入的函式所產生的程式碼會比較沒有效率比直接呼叫函式。 當您使用選項編譯時，不會出現這個警告[/clr](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
 如需詳細資訊匯入和匯出資料宣告，請參閱 < [dllexport、 dllimport](../../cpp/dllexport-dllimport.md)。  
  
## <a name="example"></a>範例  
 連結下列兩個模組，將會產生 LNK4049。 第一個模組會產生包含單一的匯出函式的物件檔案。  
  
```  
// LNK4049a.cpp  
// compile with: /c  
  
__declspec(dllexport) int func()   
{  
   return 3;  
}  
```  
  
## <a name="example"></a>範例  
 第二個模組會產生包含匯出在第一個模組中，搭配內此函式呼叫之函式的向前宣告的物件檔案`main`函式。 連結的第一個模組使用此模組將會產生 LNK4049。 移除`__declspec(dllimport)`宣告將會解決這個警告。  
  
```  
// LNK4049b.cpp  
// compile with: /link /WX /LTCG LNK4049a.obj  
// LNK4049 expected  
  
__declspec(dllimport) int func();  
// try the following line instead  
// int func();  
  
int main()  
{  
   return func();  
}  
```  
  
## <a name="see-also"></a>請參閱  
 [連結器工具警告 LNK4217](../../error-messages/tool-errors/linker-tools-warning-lnk4217.md)   
 [dllexport、dllimport](../../cpp/dllexport-dllimport.md)