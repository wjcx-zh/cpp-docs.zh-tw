---
title: "MSG 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSG"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MSG 結構"
ms.assetid: dc166d27-9423-41f1-9599-5ba76d2f0138
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MSG 結構
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`MSG` 結構包含來自執行緒之訊息佇列的訊息資訊。  
  
## 語法  
  
```  
  
      typedef struct tagMSG {     // msg    
   HWND hwnd;  
   UINT message;  
   WPARAM wParam;  
   LPARAM lParam;  
   DWORD time;  
   POINT pt;  
} MSG;  
```  
  
#### 參數  
 *hwnd*  
 識別視窗程序會接收訊息的視窗。  
  
 `message`  
 指定訊息號碼。  
  
 `wParam`  
 指定訊息的其他資訊。  確切意義取決於訊息成員的值。  
  
 `lParam`  
 指定訊息的其他資訊。  確切意義取決於訊息成員的值。  
  
 `time`  
 指定公佈訊息的時間。  
  
 `pt`  
 當公佈訊息，指定游標位置，螢幕座標的。  
  
## 需求  
 **Header:** 中  
  
## 請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)