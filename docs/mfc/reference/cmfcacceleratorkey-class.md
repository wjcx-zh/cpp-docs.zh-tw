---
title: "CMFCAcceleratorKey Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCAcceleratorKey"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCAcceleratorKey class"
ms.assetid: d140fbf7-23db-45ea-a63e-414a5ec7b3d5
caps.latest.revision: 36
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 38
---
# CMFCAcceleratorKey Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

實作虛擬按鍵對應和格式化的 Helper 類別。  
  
## 語法  
  
```  
class CMFCAcceleratorKey : public CObject  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCAcceleratorKey::CMFCAcceleratorKey](../Topic/CMFCAcceleratorKey::CMFCAcceleratorKey.md)|建構 `CMFCAcceleratorKey` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCAcceleratorKey::Format](../Topic/CMFCAcceleratorKey::Format.md)|轉譯 ACCEL 結構是它的視覺化表示。|  
|[CMFCAcceleratorKey::SetAccelerator](../Topic/CMFCAcceleratorKey::SetAccelerator.md)|設定 `CMFCAcceleratorKey` 物件的快速鍵。|  
  
## 備註  
 也稱為快速鍵是快速鍵。  如果您想要顯示使用者輸入的鍵盤快速鍵， [CMFCAcceleratorKeyAssignCtrl Class](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) 對應鍵盤快速鍵，例如 Alt\+Shift\+S，為自訂文字格式，例如「ALT \+ SHIFT \+ S」。  每個 `CMFCAcceleratorKey` 物件對應至單一快速鍵將文字格式化。  
  
 如需如何使用快速鍵和快速鍵對應表的詳細資訊，請參閱[CKeyboardManager Class](../../mfc/reference/ckeyboardmanager-class.md)。  
  
## 範例  
 下列範例示範如何建構 `CMFCAcceleratorKey` 物件及其使用方式 `Format` 方法。  
  
 [!code-cpp[NVC_MFC_RibbonApp#30](../../mfc/reference/codesnippet/CPP/cmfcacceleratorkey-class_1.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md)  
  
## 需求  
 **標題:** afxacceleratorkey.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CKeyboardManager Class](../../mfc/reference/ckeyboardmanager-class.md)