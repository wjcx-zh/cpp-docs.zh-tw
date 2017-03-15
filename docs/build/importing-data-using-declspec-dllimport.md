---
title: "使用 __declspec(dllimport) 匯入資料 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "dllimport"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec(dllimport) 關鍵字 [C++]"
  - "dllimport 屬性 [C++], 資料匯入"
  - "匯入資料 [C++]"
  - "匯入 DLL [C++], __declspec(dllimport)"
ms.assetid: 0ae70b39-87c7-4181-8be9-e786e0db60b0
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 使用 __declspec(dllimport) 匯入資料
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在資料情況下，使用 **\_\_declspec\(dllimport\)** 是移除間接傳遞層的便利項目。  您仍然需要在從 DLL 匯入資料時檢視匯入位址表。  在 **\_\_declspec\(dllimport\)** 之前，這是指在存取從 DLL 匯出的資料時，您必須記得要執行其他的間接傳遞層級：  
  
```  
// project.h  
#ifdef _DLL   // If accessing the data from inside the DLL  
   ULONG ulDataInDll;  
  
#else         // If accessing the data from outside the DLL  
   ULONG *ulDataInDll;  
#endif  
```  
  
 接著您可以在您的.DEF 檔裡匯出資料：  
  
```  
// project.def  
LIBRARY project  
EXPORTS  
   ulDataInDll   CONSTANT  
```  
  
 並且由 DLL 的外部存取：  
  
```  
if (*ulDataInDll == 0L)   
{  
   // Do stuff here  
}  
```  
  
 編譯器會在您將資料標記成 **\_\_declspec\(dllimport\)** 自動為您產生間接傳遞程式碼。  您無須擔心上述步驟。  如同前述，建置 DLL 時請勿在資料上使用 **\_\_declspec\(dllimport\)** 宣告。  DLL 內的函式不會使用匯入位址表來存取資料物件；因此，不會有其他的間接傳遞層級存在。  
  
 若要從 DLL 自動匯出資料，請使用這個宣告：  
  
```  
__declspec(dllexport) ULONG ulDataInDLL;  
```  
  
## 請參閱  
 [匯入至應用程式](../build/importing-into-an-application.md)