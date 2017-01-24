---
title: "CMFCImageEditorDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCImageEditorDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCImageEditorDialog class"
ms.assetid: 6a7d08f3-1ec2-4062-9b79-a0c2776b58d1
caps.latest.revision: 24
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCImageEditorDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCImageEditorDialog` 類別支援影像編輯器對話方塊。  
  
## 語法  
  
```  
class CMFCImageEditorDialog : public CDialogEx  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCImageEditorDialog::CMFCImageEditorDialog](../Topic/CMFCImageEditorDialog::CMFCImageEditorDialog.md)|建構 `CMFCImageEditorDialog` 物件。|  
  
## 備註  
 `CMFCImageEditorDialog` 類別提供的對話方塊:  
  
-   您可以使用修改影像中的個別像素的影像區域。  
  
-   修改圖片區域的像素繪圖工具。  
  
-   指定繪圖工具之色彩的色板。  
  
-   顯示要編輯的效果的預覽區域。  
  
 下圖顯示 \[影像編輯器\] 對話方塊。  
  
 ![CMFCImageEditorDialog 對話方塊](../../mfc/reference/media/imageedit.png "ImageEdit")  
  
 其中一種方式是使用 `CMFCImageEditorDialog` 物件會透過它要編輯的 `CBitmap` 影像。   不要建立大型影像，因為編輯區域的影像具有大小限制，而且調整邏輯像素大小來填滿區域。  `DoModal` 呼叫方法以啟動強制回應對話方塊。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDialogEx](../../mfc/reference/cdialogex-class.md)  
  
 [CMFCImageEditorDialog](../../mfc/reference/cmfcimageeditordialog-class.md)  
  
## 需求  
 **標題:** afximageeditordialog.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md)