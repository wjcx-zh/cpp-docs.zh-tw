---
title: "CWndClassInfo Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CWndClassInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWndClassInfo class"
ms.assetid: c36fe7e1-75f1-4cf5-a06f-9f59c43fe6fb
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CWndClassInfo Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會註冊視窗類別的資訊的方法。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
class CWndClassInfo  
  
```  
  
## Members  
  
### 公用方法  
  
|||  
|-|-|  
|[註冊](../Topic/CWndClassInfo::Register.md)|註冊視窗類別。|  
  
### 資料成員  
  
|||  
|-|-|  
|[m\_atom](../Topic/CWndClassInfo::m_atom.md)|唯一識別已登錄的視窗類別。|  
|[m\_bSystemCursor](../Topic/CWndClassInfo::m_bSystemCursor.md)|指定游標資源是否參考系統游標或加入至模組資源中的游標。|  
|[m\_lpszCursorID](../Topic/CWndClassInfo::m_lpszCursorID.md)|指定游標資源的名稱。|  
|[m\_lpszOrigName](../Topic/CWndClassInfo::m_lpszOrigName.md)|包含現有視窗類別的名稱。|  
|[m\_szAutoName](../Topic/CWndClassInfo::m_szAutoName.md)|保留視窗類別的一個 ATL 所產生的名稱。|  
|[m\_wc](../Topic/CWndClassInfo::m_wc.md)|維護視窗在 **WNDCLASSEX** 結構的類別資訊。|  
|[pWndProc](../Topic/CWndClassInfo::pWndProc.md)|對現有視窗的視窗程序的按分類。|  
  
## 備註  
 `CWndClassInfo` 處理視窗類別的相關資訊。  您透過三個巨集通常會使用 `CWndClassInfo` ， `DECLARE_WND_CLASS`、 `DECLARE_WND_CLASS_EX`或 `DECLARE_WND_SUPERCLASS`其中之一，如下表所示:  
  
|巨集|描述|  
|--------|--------|  
|[DECLARE\_WND\_CLASS](../Topic/DECLARE_WND_CLASS.md)|`CWndClassInfo` 新的視窗類別的暫存器資訊。|  
|[DECLARE\_WND\_CLASS\_EX](../Topic/DECLARE_WND_CLASS_EX.md)|`CWndClassInfo` 新的視窗類別的暫存器資訊，包括類別的界限。|  
|[DECLARE\_WND\_SUPERCLASS](../Topic/DECLARE_WND_SUPERCLASS.md)|`CWndClassInfo` 根據現有的類別，但的視窗類別的暫存器資訊使用不同的視窗程序。  這項技術稱為 superclassing。|  
  
 根據預設， [CWindowImpl](../../atl/reference/cwindowimpl-class.md) 包括 `DECLARE_WND_CLASS` 巨集來建立新的視窗類別的視窗。  DECLARE\_WND\_CLASS 提供控制項的預設樣式和背景色彩。  如果您要指定樣式和背景色彩，從 `CWindowImpl` 衍生您的類別並包含 `DECLARE_WND_CLASS_EX` 巨集在類別定義中。  
  
 如果您想要以現有視窗類別的  視窗中，從 `CWindowImpl` 衍生您的類別並包含 `DECLARE_WND_SUPERCLASS` 巨集在類別定義中。  例如：  
  
 [!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/CPP/cwndclassinfo-class_1.h)]  
  
 如需視窗類別的詳細資訊，請參閱 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [視窗類別](http://msdn.microsoft.com/library/windows/desktop/ms632596) 。  
  
 如需使用  視窗的詳細資訊，請參閱 ATL 本文 [ATL 視窗類別](../../atl/atl-window-classes.md)。  
  
## 需求  
 **Header:** atlwin.h  
  
## 請參閱  
 [CComControl Class](../../atl/reference/ccomcontrol-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)