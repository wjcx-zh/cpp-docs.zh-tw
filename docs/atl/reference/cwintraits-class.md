---
title: "CWinTraits Class | Microsoft Docs"
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
  - "CWinTraits"
  - "CMDIChildWinTraits"
  - "ATL.CWinTraits"
  - "CFrameWinTraits"
  - "ATL::CWinTraits"
  - "CControlWinTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CControlWinTraits class"
  - "CFrameWinTraits class"
  - "CMDIChildWinTraits class"
  - "CWinTraits class"
  - "window styles, default values for ATL"
ms.assetid: f78f486e-6d9c-42c6-8e86-371e05aa7e59
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CWinTraits Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示建立視窗物件時，這個類別會提供標準化樣式提供方法所使用。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
      template <  
DWORD t_dwStyle= 0,  
DWORD t_dwExStyle= 0  
>  
class CWinTraits  
```  
  
#### 參數  
 `t_dwStyle`  
 預設標準視窗樣式。  
  
 `t_dwExStyle`  
 預設延伸視窗樣式。  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CWinTraits::GetWndExStyle](../Topic/CWinTraits::GetWndExStyle.md)|\(靜態\) 擷取 `CWinTraits` 物件的延伸樣式。|  
|[CWinTraits::GetWndStyle](../Topic/CWinTraits::GetWndStyle.md)|\(靜態\) 擷取 `CWinTraits` 物件的標準模式。|  
  
## 備註  
 這個類別會提供 [視窗特性](../../atl/understanding-window-traits.md) 標準化用於 ATL 視窗物件建立的樣式提供簡單的方法。  使用這個類別的特製化當做樣板參數傳遞給 [CWindowImpl](../../atl/reference/cwindowimpl-class.md) 或類別的 ATL 的視窗類別指定標準的預設和用於該視窗類別執行個體的延伸樣式。  
  
 請使用這個範本，當您想要提供所要使用的預設視窗樣式時，只有在其他模式在 \[ [CWindowImpl::Create](../Topic/CWindowImpl::Create.md)時的呼叫未指定。  
  
 ATL 的視窗樣式的常用的組合提供這個樣板的三個預先定義的特製化:  
  
 `CControlWinTraits`  
 設計為標準控制項的視窗。  使用下列標準樣式: **WS\_CHILD**、 **WS\_VISIBLE**、 **WS\_CLIPCHILDREN**和 **WS\_CLIPSIBLINGS**。  沒有延伸樣式。  
  
 `CFrameWinTraits`  
 是專為標準框架視窗。  使用的標準模式包括: **WS\_OVERLAPPEDWINDOW**、 **WS\_CLIPCHILDREN**和 **WS\_CLIPSIBLINGS**。  使用的延伸樣式包括: **WS\_EX\_APPWINDOW** 和 **WS\_EX\_WINDOWEDGE**。  
  
 `CMDIChildWinTraits`  
 是專為標準 MDI 子視窗。  使用的標準模式包括: **WS\_OVERLAPPEDWINDOW**、 **WS\_CHILD**、 **WS\_VISIBLE**、 **WS\_CLIPCHILDREN**和 **WS\_CLIPSIBLINGS**。  使用的延伸樣式包括: **WS\_EX\_MDICHILD**。  
  
 如果您想要確保特定模式的視窗類別的所有執行個體設定屬性，以允許其他樣式設定根據每個執行個體而定，使用 [CWinTraitsOR](../../atl/reference/cwintraitsor-class.md) 時。  
  
## 需求  
 **Header:** atlwin.h  
  
## 請參閱  
 [Class Members](http://msdn.microsoft.com/zh-tw/dbe6a147-3f01-4aea-a3fb-fe6ebadc31f8)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [Understanding Window Traits](../../atl/understanding-window-traits.md)