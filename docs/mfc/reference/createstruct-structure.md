---
title: "CREATESTRUCT 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CREATESTRUCT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CREATESTRUCT 結構"
ms.assetid: 028c7b5e-4fdc-48da-a550-d3e4f9e6cc85
caps.latest.revision: 14
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CREATESTRUCT 結構
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CREATESTRUCT` 結構定義初始化參數傳遞至應用程式的視窗程序。  
  
## 語法  
  
```  
  
      typedef struct tagCREATESTRUCT {  
   LPVOID lpCreateParams;  
   HANDLE hInstance;  
   HMENU hMenu;  
   HWND hwndParent;  
   int cy;  
   int cx;  
   int y;  
   int x;  
   LONG style;  
   LPCSTR lpszName;  
   LPCSTR lpszClass;  
   DWORD dwExStyle;  
} CREATESTRUCT;  
```  
  
#### 參數  
 `lpCreateParams`  
 要使用的資料點建立視窗。  
  
 `hInstance`  
 識別擁有新視窗模組的模組執行個體控制代碼。  
  
 `hMenu`  
 識別新視窗時所用的功能表。  如果子視窗，包含整數 ID.  
  
 `hwndParent`  
 識別擁有新視窗的視窗。  如果新視窗是最上層視窗，這個成員是 **NULL** 。  
  
 `cy`  
 指定新視窗的高度。  
  
 `cx`  
 指定新視窗的寬度。  
  
 `y`  
 指定新視窗左上角的 Y 座標。  如果新視窗是子視窗，座標則是相對於父視窗；否則座標是相對於螢幕原點。  
  
 `x`  
 指定新視窗左上角的 X 座標。  如果新視窗是子視窗，座標則是相對於父視窗；否則座標是相對於螢幕原點。  
  
 `style`  
 指定新視窗的 [樣式](../../mfc/reference/styles-used-by-mfc.md)。  
  
 `lpszName`  
 要指定新視窗的名稱以 Null 結束之字串的點。  
  
 `lpszClass`  
 要指定新視窗的視窗類別名稱以 Null 結束之字串的點 \( [名稱](http://msdn.microsoft.com/library/windows/desktop/ms633576) 結構；如需詳細資訊，請參閱 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]\)。  
  
 `dwExStyle`  
 為新視窗指定 [延伸樣式](../../mfc/reference/extended-window-styles.md) 。  
  
## 需求  
 **標頭：** winuser.h  
  
## 請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnCreate](../Topic/CWnd::OnCreate.md)