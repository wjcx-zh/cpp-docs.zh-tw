---
title: "CWinTraitsOR Class | Microsoft Docs"
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
  - "ATL.CWinTraitsOR"
  - "ATL::CWinTraitsOR"
  - "CWinTraitsOR"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWinTraitsOR class"
  - "window styles, default values for ATL"
ms.assetid: 1eb7b1e8-a9bd-411b-a30a-35a8a10af989
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CWinTraitsOR Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示建立視窗物件時，這個類別會提供標準化樣式提供方法所使用。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
      template <  
DWORD t_dwStyle= 0,  
DWORDt_dwExStyle= 0,  
class TWinTraits = CControlWinTraits   
>  
class CWinTraitsOR  
```  
  
#### 參數  
 `t_dwStyle`  
 預設的視窗樣式。  
  
 `t_dwExStyle`  
 預設延伸視窗樣式。  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CWinTraitsOR::GetWndExStyle](../Topic/CWinTraitsOR::GetWndExStyle.md)|擷取 `CWinTraitsOR` 物件的延伸樣式。|  
|[CWinTraitsOR::GetWndStyle](../Topic/CWinTraitsOR::GetWndStyle.md)|擷取 `CWinTraitsOR` 物件的標準模式。|  
  
## 備註  
 這個類別會提供 [視窗特性](../../atl/understanding-window-traits.md) 標準化用於 ATL 視窗物件建立的樣式提供簡單的方法。  使用這個類別的特製化當做樣板參數傳遞給 [CWindowImpl](../../atl/reference/cwindowimpl-class.md) 或類別的 ATL 的視窗類別指定最小值為該視窗類別的執行個體會使用設定的標準和延伸樣式。  
  
 請使用這個樣板的特製化，如果您想要確保特定模式的視窗類別的所有執行個體設定屬性，以允許其他樣式設定會根據在的每一個執行個體而定。 [CWindowImpl::Create](../Topic/CWindowImpl::Create.md)時。  
  
 如果您要提供所要使用的預設視窗樣式，只有在其他模式在 \[ `CWindowImpl::Create`時的呼叫沒有指定，請使用 [CWinTraits](../../atl/reference/cwintraits-class.md) 。  
  
## 需求  
 **Header:** atlwin.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)   
 [Understanding Window Traits](../../atl/understanding-window-traits.md)