---
title: "CDialogImpl Class | Microsoft Docs"
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
  - "CDialogImpl"
  - "ATL.CDialogImpl"
  - "ATL::CDialogImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDialogImpl class"
  - "對話方塊, ATL"
ms.assetid: d430bc7b-8a28-4ad3-9507-277bdd2c2c2e
caps.latest.revision: 25
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDialogImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會建立強制回應或非強制回應對話方塊的方法。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
      template <  
class T,  
class TBase= CWindow   
>  
class ATL_NO_VTABLE CDialogImpl :  
public CDialogImplBaseT< TBase>  
```  
  
#### 參數  
 `T`  
 您的類別，衍生自 `CDialogImpl`。  
  
 *TBase*  
 您的新類別的基底類別。  預設基底類別是 [CWindow](../../atl/reference/cwindow-class.md)。  
  
## Members  
  
### 方法  
  
|||  
|-|-|  
|[Create](../Topic/CDialogImpl::Create.md)|建立非強制回應對話方塊。|  
|[DestroyWindow](../Topic/CDialogImpl::DestroyWindow.md)|終結非強制回應對話方塊。|  
|[DoModal](../Topic/CDialogImpl::DoModal.md)|建立強制回應對話方塊。|  
|[EndDialog](../Topic/CDialogImpl::EndDialog.md)|終結強制回應對話方塊。|  
  
### CDialogImplBaseT 方法  
  
|||  
|-|-|  
|[GetDialogProc](../Topic/CDialogImpl::GetDialogProc.md)|傳回目前的對話方塊程序。|  
|[MapDialogRect](../Topic/CDialogImpl::MapDialogRect.md)|將指定之矩形的對話方塊單位篩選單位 \(像素\)。|  
|[OnFinalMessage](../Topic/CDialogImpl::OnFinalMessage.md)|最後一個呼叫在接收訊息之後，通常 `WM_NCDESTROY`。|  
  
### 靜態函式  
  
|||  
|-|-|  
|[DialogProc](../Topic/CDialogImpl::DialogProc.md)|處理傳送至  對話方塊。|  
|[StartDialogProc](../Topic/CDialogImpl::StartDialogProc.md)|呼叫時，第一個訊息接收處理傳送至  對話方塊。|  
  
## 備註  
 您可以 `CDialogImpl` 建立強制回應或非強制回應對話方塊。  `CDialogImpl` 提供對話方塊程序，使用預設的訊息對應會用來導向訊息給適當的處理常式。  
  
 基底類別解構函式 **~CWindowImplRoot** 保證視窗在終結物件之前會消失。  
  
 `CDialogImpl` 從 **CDialogImplBaseT**衍生，從 **CWindowImplRoot**又衍生自。  
  
> [!NOTE]
>  您的類別必須定義指定對話方塊樣板資源 ID. 的 **IDD** 成員  例如， ATL 專案精靈會自動將下列行加入至類別:  
  
 [!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/CPP/cdialogimpl-class_1.h)]  
  
 其中 `MyDlg` 是精靈中的 \[**名稱**\] 頁面項目的 **Short name** 。  
  
|如需詳細資訊|請參閱|  
|------------|---------|  
|建立控制項|[ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)|  
|使用 ATL 中的對話方塊|[ATL 視窗類別](../../atl/atl-window-classes.md)|  
|ATL 專案精靈|[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)|  
|對話方塊|[對話方塊](http://msdn.microsoft.com/library/windows/desktop/ms632588) 和後續的主題。 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]|  
  
## 需求  
 **Header:** atlwin.h  
  
## 請參閱  
 [BEGIN\_MSG\_MAP](../Topic/BEGIN_MSG_MAP.md)   
 [Class Overview](../../atl/atl-class-overview.md)