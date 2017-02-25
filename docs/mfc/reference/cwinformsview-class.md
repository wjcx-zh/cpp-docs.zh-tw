---
title: "CWinFormsView Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CWinFormsView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWinFormsView class"
  - "MFC [C++], Windows Form 支援"
  - "Windows Form [C++], MFC 支援"
ms.assetid: d597e397-6529-469b-88f5-7f65a6b9e895
caps.latest.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 28
---
# CWinFormsView Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供裝載 Windows Form 控制項的一般功能為 MFC 檢視。  
  
## 語法  
  
```  
class CWinFormsView : public CView;  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CWinFormsView::CWinFormsView](../Topic/CWinFormsView::CWinFormsView.md)|建構 `CWinFormsView` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CWinFormsView::GetControl](../Topic/CWinFormsView::GetControl.md)|擷取指標對 Windows Form 控制項。|  
  
### 公用運算子  
  
|名稱||  
|--------|-|  
|[CWinFormsView::operator Control^](../Topic/CWinFormsView::operator%20Control%5E.md)|轉換為型別為指標對 Windows Form 控制項。|  
  
## 備註  
 MFC 使用 `CWinFormsView` 類別來裝載 \(Host\) MFC 檢視內的 .NET Framework Windows Form 控制項。  控制項是原生 \(Native\) 檢視的子系並佔用 MFC 檢視的整個工作區 \(Client Area\)。  結果類似 `CFormView` 檢視，可以讓您利用 Windows Form 設計工具和執行階段來建立豐富的表單架構檢視。  
  
 如需使用 Windows Form 的詳細資訊，請參閱 [在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。  
  
> [!NOTE]
>  MFC Windows Form 整合只有在和 MFC 的專案中才有作用 \(有定義 AFXDLL 的專案動態連接。  
  
> [!NOTE]
>  CWinFormsView 不支援 MFC 分隔視窗 \([CSplitterWnd Class](../../mfc/reference/csplitterwnd-class.md)\)。  目前只有 Windows Form 分隔器控制項 \(<xref:System.Windows.Forms.Splitter>\) 支援。  
  
## 需求  
 **標題:** afxwinforms.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CWinFormsControl Class](../../mfc/reference/cwinformscontrol-class.md)   
 [CWinFormsDialog Class](../../mfc/reference/cwinformsdialog-class.md)   
 [CFormView Class](../../mfc/reference/cformview-class.md)