---
title: "明確連結 | Microsoft Docs"
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
  - "明確連結 [C++]"
ms.assetid: 1e13d960-a195-4e6d-9864-7d8f3a701f4b
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 明確連結
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用明確連結時，應用程式必須製作函式呼叫，以便在執行階段明確地載入 DLL。  為了明確地連結 DLL，應用程式必須：  
  
-   呼叫 **LoadLibrary** \(或類似函式\) 來載入 DLL 並且獲得模組控制代碼。  
  
-   呼叫 **GetProcAddress** 以便獲得每個應用程式要呼叫的匯出函式之函式指標。  因為應用程式是經由指標呼叫 DLL 的函式，所以編譯器不會產生外部參考，如此一來，就不需要連結匯入程式庫。  
  
-   在使用完 DLL 時呼叫 **FreeLibrary**。  
  
 例如：  
  
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
  
## 您想要執行甚麼工作？  
  
-   [隱含連結](../build/linking-implicitly.md)  
  
-   [判斷要使用哪一個連結方法](../build/determining-which-linking-method-to-use.md)  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [LoadLibrary 和 AfxLoadLibrary](../build/loadlibrary-and-afxloadlibrary.md)  
  
-   [GetProcAddress](../build/getprocaddress.md)  
  
-   [FreeLibrary 和 AfxFreeLibrary](../build/freelibrary-and-afxfreelibrary.md)  
  
-   [Windows 用來找出 DLL 的搜尋路徑](../build/search-path-used-by-windows-to-locate-a-dll.md)  
  
## 請參閱  
 [將可執行檔連結至 DLL](../build/linking-an-executable-to-a-dll.md)