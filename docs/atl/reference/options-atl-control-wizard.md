---
title: "選項, ATL 控制項精靈 | Microsoft Docs"
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
  - "vc.codewiz.class.atl.control.options"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL 控制項精靈, 選項"
ms.assetid: 4607c51a-992d-433e-9281-919c6f519a3d
caps.latest.revision: 14
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 選項, ATL 控制項精靈
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在這裡插入「搜尋結果」摘要。  
  
 您可使用此精靈頁面來定義您建立控制項的型別及其包含的介面支援層級。  
  
## UIElement 清單  
 **控制項型別**  
 您要建立的控制項型別。  
  
-   **標準控制項：ActiveX 控制項**  
  
-   \[**複合控制項**\]：可包含 \(類似對話方塊\) 其他 ActiveX 控制項或 Windows 控制項的 ActiveX 控制項。  複合控制項包含下列部分：  
  
    -   實作複合控制項的對話方塊範本。  
  
    -   當叫用 \(Invoke\) 時會自動登錄複合控制項的自訂資源 REGISTRY。  
  
    -   實作複合控制項的 C\+\+ 類別。  
  
    -   複合控制項公開的 COM 介面。  
  
    -   包含複合控制項的 HTML 測試網頁。  
  
     依照預設，這個控制項會將 [CComControlBase::m\_bWindowOnly](../Topic/CComControlBase::m_bWindowOnly.md) 設定為 true，表示這是視窗型控制項。  它會實作接收對應。  如需詳細資訊，請參閱 [DHTML 控制項的支援](../../atl/atl-support-for-dhtml-controls.md)。  
  
-   \[**DHTML 控制項**\]：ATL DHTML 控制項使用 HTML 指定使用者介面。  DHTML UI 類別包含 COM 對應。  依照預設，這個控制項會將 [CComControlBase::m\_bWindowOnly](../Topic/CComControlBase::m_bWindowOnly.md) 設定為 true，表示這是視窗型控制項。  
  
     如需詳細資訊，請參閱 [Identifying the Elements of the DHTML Control Project](../../atl/identifying-the-elements-of-the-dhtml-control-project.md)。  
  
 **最小控制項**  
 只支援多數容器絕對需要的介面。  您可為任何控制項型別設定 \[**最小控制項**\]：建立最小標準控制項、最小複合控制項或最小 DHTML 控制項。  
  
 **Aggregation**  
 為您建立的控制項加入彙總 \(Aggregation\) 支援。  如需詳細資訊，請參閱 [Aggregation](../../atl/aggregation.md)。  
  
-   \[**是**\]：建立可彙總的控制項。  
  
-   \[**否**\]：建立無法彙總的控制項。  
  
-   \[**僅**\]：建立只能透過彙總執行個體化的控制項。  
  
 **執行緒模型**  
 指定控制項使用的執行緒模型。  
  
-   \[**單一**\]：控制項只在主要 COM 執行緒中執行。  
  
-   \[**Apartment**\]：控制項可在任何單一執行緒 Apartment 中建立。  預設值。  
  
 **介面**  
 這個控制項公開給容器的介面類型。  
  
-   \[**雙重**\]：建立透過 `IDispatch` 和直接透過 VTBL 公開 \(Expose\) 屬性和方法的介面。  
  
-   \[**自訂**\]：建立直接透過 VTBL 公開方法的介面。  
  
     如果您選取 \[**自訂**\]，您就可指定控制項是 \[**Automation 相容**\]。  如果您選取 \[**Automation 相容**\]，則精靈會將 [oleautomation](../../windows/oleautomation.md) 屬性加入至 IDL 內的介面，接著 oleaut32.dll 中的通用封送處理器就能夠封送處理介面。  如需詳細資訊，請參閱 [!INCLUDE[winsdkshort](../../atl/reference/includes/winsdkshort_md.md)] 中的[封送處理詳細資訊](http://msdn.microsoft.com/library/windows/desktop/ms692621)。  
  
     除此之外，如果您選取 \[**Automation 相容**\]，則控制項中所有方法的所有參數都必須是 **VARIANT** 相容的。  
  
 **支援**  
 為控制項設定其他支援。  
  
-   \[**啟用連接點**\]：從 [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md) 衍生物件的類別並允許它公開來源介面，為您的物件啟用連接點 \(Connection Point\)。  
  
-   **授權**：將支援加入控制項以[行授權](http://msdn.microsoft.com/library/windows/desktop/ms690543)。  授權控制項只能在用戶端機器具有正確使用權時裝載。  
  
## 請參閱  
 [ATL 控制項精靈](../../atl/reference/atl-control-wizard.md)