---
title: "使用 .DEF 檔匯入 | Microsoft Docs"
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
  - ".def 檔案 [C++], 匯入"
  - "def 檔案 [C++], 匯入"
  - "dllimport 屬性 [C++], DEF 檔案"
  - "DLL [C++], DEF 檔案"
  - "匯入 DLL [C++], DEF 檔案"
ms.assetid: aefdbf50-f603-488a-b0d7-ed737bae311d
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 使用 .DEF 檔匯入
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果您選擇使用 **\_\_declspec\(dllimport\)** 和 .def 檔，則您應該變更 .def 檔，使用 DATA 來取代 CONSTANT，以降低不正確的程式設計造成問題的可能性：  
  
```  
// project.def  
LIBRARY project  
EXPORTS  
   ulDataInDll   DATA  
```  
  
 下表顯示問題產生的原因。  
  
|關鍵字|在匯入程式庫裡發出|匯出|  
|---------|---------------|--------|  
|`CONSTANT`|`_imp_ulDataInDll_ulDataInDll`|`_ulDataInDll`|  
|`DATA`|`_imp_ulDataInDll`|`_ulDataInDll`|  
  
 使用 **\_\_declspec\(dllimport\)** 和 CONSTANT 會列出 .lib DLL 匯入程式庫的 `imp` 版本和未裝飾名稱 \(Undecorated Name\)，此程式庫是為允許明確連結而建立。  使用 **\_\_declspec\(dllimport\)** 和 DATA 則會列出名稱的 `imp` 版本。  
  
 如果您使用 CONSTANT，則可以使用下列任一種程式碼建構來存取 `ulDataInDll`：  
  
```  
__declspec(dllimport) ULONG ulDataInDll; /*prototype*/  
if (ulDataInDll == 0L)   /*sample code fragment*/  
```  
  
 \-或\-  
  
```  
ULONG *ulDataInDll;      /*prototype*/  
if (*ulDataInDll == 0L)  /*sample code fragment*/  
```  
  
 然而，如果您在 .def 檔中使用 DATA，則只有使用下列定義編譯的程式碼可以存取 `ulDataInDll` 變數：  
  
```  
__declspec(dllimport) ULONG ulDataInDll;  
  
if (ulDataInDll == 0L)   /*sample code fragment*/  
```  
  
 CONSTANT 是較危險的使用方式，因為如果您忘記已使用其他的間接傳遞層級，您很可能會存取到變數的匯入位址表指標 — 而不是變數本身。  這類型的問題通常會明示為存取違規，因為編譯器和連結器目前是將匯入位址表設為唯讀。  
  
 如果在 .def 檔中看到 CONSTANT，則目前的 Visual C\+\+ 連結器會發出警告說明這個情況。  使用 CONSTANT 的唯一真正理由，是您無法重新編譯某些物件檔 \(因為標頭檔在原型上未列出 **\_\_declspec\(dllimport\)**\)。  
  
## 請參閱  
 [匯入至應用程式](../build/importing-into-an-application.md)