---
title: "GetProcAddress | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetProcAddress"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DLL [C++], GetProcAddress"
  - "GetProcAddress 方法"
  - "序數匯出 [C++]"
ms.assetid: 48d14ae0-47ea-4c5d-96b1-2c158f1a26af
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# GetProcAddress
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

明確連結至 DLL 的處理序會呼叫 [GetProcAddress](http://msdn.microsoft.com/library/windows/desktop/ms683212) 來獲得 DLL 裡匯出函式的位址。  您可以使用傳回的函式指標來呼叫 DLL 函式。  **GetProcAddress** 會將 DLL 模組控制代碼 \(由 **LoadLibrary**、`AfxLoadLibrary` 或 **GetModuleHandle** 傳回\) 和您要呼叫的函式名稱或函式的匯出序數當做參數來使用。  
  
 因為 DLL 函式是經由指標呼叫，而且沒有編譯時期型別檢查，請確定函式的參數是正確的，以防止您逾越堆疊的記憶體配置和造成存取違規。  一個提供型別安全的方式是檢視匯出函式的函式原型，並為函式指標建立相符的 Typedef。  例如：  
  
```  
typedef UINT (CALLBACK* LPFNDLLFUNC1)(DWORD,UINT);  
...  
  
HINSTANCE hDLL;               // Handle to DLL  
LPFNDLLFUNC1 lpfnDllFunc1;    // Function pointer  
DWORD dwParam1;  
UINT  uParam2, uReturnVal;  
  
hDLL = LoadLibrary("MyDLL");  
if (hDLL != NULL)  
{  
   lpfnDllFunc1 = (LPFNDLLFUNC1)GetProcAddress(hDLL,  
                                           "DLLFunc1");  
   if (!lpfnDllFunc1)  
   {  
      // handle the error  
      FreeLibrary(hDLL);  
      return SOME_ERROR_CODE;  
   }  
   else  
   {  
      // call the function  
      uReturnVal = lpfnDllFunc1(dwParam1, uParam2);  
   }  
}  
```  
  
 呼叫 **GetProcAddress**  時的所需函式指定方式是根據 DLL 建置方式而決定的。  
  
 如果要連結的 DLL 是以模組定義 \(.def\) 檔建置，且序數和函式並列於 DLL 的 .def 檔之 **EXPORTS** 區段中，則您只能取得匯出序數。  相對於使用函式名稱，如果 DLL 有許多匯出函式，以匯出序數呼叫 **GetProcAddress** 會稍微快些，因為匯出序數會被當成 DLL 匯出表的索引。  有了匯出序數，**GetProcAddress** 可以直接找出函式，相反做法則是在 DLL 匯出表的函式名稱比較指定名稱。  然而，只有當您可以控制 .def 檔案裡匯出函式的序數指派時，才應該以匯出序數呼叫 **GetProcAddress**。  
  
## 您想要執行甚麼工作？  
  
-   [隱含連結](../build/linking-implicitly.md)  
  
-   [判斷要使用哪一個連結方法](../build/determining-which-linking-method-to-use.md)  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [LoadLibrary 和 AfxLoadLibrary](../build/loadlibrary-and-afxloadlibrary.md)  
  
-   [\<caps:sentence id\="tgt17" sentenceid\="8c920606bb67e2587dd3c3e5cf977593" class\="tgtSentence"\>FreeLibrary\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms683152)  
  
-   [使用 .DEF 檔從 DLL 匯出](../build/exporting-from-a-dll-using-def-files.md)  
  
## 請參閱  
 [Visual C\+\+ 中的 DLL](../build/dlls-in-visual-cpp.md)