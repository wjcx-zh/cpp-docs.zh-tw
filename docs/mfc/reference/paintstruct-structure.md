---
title: "PAINTSTRUCT 結構 | Microsoft Docs"
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
  - "PAINTSTRUCT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PAINTSTRUCT 結構"
ms.assetid: 81ce4993-3e89-43b2-8c98-7946f1314d24
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# PAINTSTRUCT 結構
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`PAINTSTRUCT` 結構包含可用於繪製視窗工作區的資訊。  
  
## 語法  
  
```  
  
      typedef struct tagPAINTSTRUCT {  
   HDC hdc;  
   BOOL fErase;  
   RECT rcPaint;  
   BOOL fRestore;  
   BOOL fIncUpdate;  
   BYTE rgbReserved[16];  
} PAINTSTRUCT;  
```  
  
#### 參數  
 *hdc*  
 識別用來繪製的顯示內容。  
  
 *fErase*  
 指定背景是否需要重新繪製。  如果應用程式應該重新繪製背景，它不是 0。  應用程式負責繪製背景執行，如果視窗是視窗類別建立，而不使用背景筆刷 \(請參閱 [名稱](http://msdn.microsoft.com/library/windows/desktop/ms633576) 結構的成員 **hbrBackground** 的說明 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]中的\)。  
  
 *rcPaint*  
 指定繪製要求矩形的左上角和右下角。  
  
 *fRestore*  
 保留的成員。  視窗在內部使用。  
  
 *fIncUpdate*  
 保留的成員。  視窗在內部使用。  
  
 *rgbReserved\[16\]*  
 保留的成員。  視窗內部使用的保留的記憶體區塊。  
  
## 需求  
 **Header:** winuser.h  
  
## 請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CPaintDC::m\_ps](../Topic/CPaintDC::m_ps.md)