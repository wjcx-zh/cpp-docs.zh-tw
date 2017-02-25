---
title: "連結器工具警告 LNK4049 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4049"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4049"
ms.assetid: 5fd5fb24-c860-4149-a557-0ac26a65d97c
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# 連結器工具警告 LNK4049
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本機定義的符號 'symbol' 已匯入  
  
 符號同時自程式匯出及匯入程式。  
  
 當您在一個目的檔 \(Object File\) 中使用 `__declspec(dllexport)` 儲存類別屬性來宣告符號，並在另一個目的檔中使用 `__declspec(dllimport)` 屬性參考該符號時，連結器就會產生這個警告。  
  
 警告 LNK4049 是[連結器工具警告 LNK4217](../../error-messages/tool-errors/linker-tools-warning-lnk4217.md) 比較普通的版本。  當連結器無法決定參考匯入符號的來源函式時，就會產生警告 LNK4049。  
  
 會產生 LNK4049，而不是產生 LNK4217 的常見原因如下：  
  
-   使用 [\/INCREMENTAL](../../build/reference/incremental-link-incrementally.md) 選項來執行累加連結。  
  
-   使用 [\/LTCG](../../build/reference/ltcg-link-time-code-generation.md) 選項來執行整個程式最佳化。  
  
 若要解決 LNK4049，請嘗試下列任一種方法：  
  
-   從觸發 LNK4049 之符號的向前宣告中移除 `__declspec(dllimport)` 名稱宣告。  您可以使用 **DUMPBIN** 公用程式，在二進位檔映像中搜尋符號。  **DUMPBIN \/SYMBOLS** 參數會顯示映像的 COFF 系統資料表。  如需 **DUMPBIN** 公用程式的詳細資訊，請參閱 [DUMPBIN 參考](../../build/reference/dumpbin-reference.md)。  
  
-   暫時停用累加連結和整個程式最佳化。  重新編譯應用程式將會產生警告 LNK4217，其中包含參考匯入符號的來源函式名稱。  將 `__declspec(dllimport)` 宣告從匯入符號中移除，並依需要啟用累加連結或整個程式最佳化。  
  
 雖然最後產生的程式碼可以正常運作，但就效率而言，直接呼叫函式會優於所產生用來呼叫匯入函式的程式碼。  使用選項 [\/clr](../../build/reference/clr-common-language-runtime-compilation.md) 進行編譯時，不會出現這個警告。  
  
 如需有關匯入和匯出資料宣告的詳細資訊，請參閱 [dllexport、dllimport](../../cpp/dllexport-dllimport.md)。  
  
## 範例  
 連結下列兩個模組將會產生 LNK4049。  第一個模組會產生只包含一個匯出函式的目的檔。  
  
```  
// LNK4049a.cpp  
// compile with: /c  
  
__declspec(dllexport) int func()   
{  
   return 3;  
}  
```  
  
## 範例  
 第二個模組所產生的目的檔則會包含對第一個模式中匯出之函式的向前宣告，以及在 `main` 函式中呼叫這個函式的呼叫。  將這個模組與第一個模組連結，將會產生 LNK4049。  移除 `__declspec(dllimport)` 宣告就可以解決這個警告。  
  
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
  
## 請參閱  
 [連結器工具警告 LNK4217](../../error-messages/tool-errors/linker-tools-warning-lnk4217.md)   
 [dllexport、dllimport](../../cpp/dllexport-dllimport.md)