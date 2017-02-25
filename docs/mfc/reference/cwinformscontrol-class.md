---
title: "CWinFormsControl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CWinFormsControl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWinFormsControl class"
  - "MFC [C++], Windows Form 支援"
  - "Windows Form [C++], MFC 支援"
ms.assetid: 6406dd7b-fb89-4a18-ac3a-c010d6b6289a
caps.latest.revision: 28
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 30
---
# CWinFormsControl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供裝載 Windows Form 控制項的基本功能。  
  
## 語法  
  
```  
template<class TManagedControl>  
class CWinFormsControl : public CWnd  
```  
  
#### 參數  
 `TManagedControl`  
 在 MFC 應用程式中顯示的 .NET Framework Windows Form 控制項。  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CWinFormsControl::CWinFormsControl](../Topic/CWinFormsControl::CWinFormsControl.md)|建構 MFC Windows Form 控制項包裝函式物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CWinFormsControl::CreateManagedControl](../Topic/CWinFormsControl::CreateManagedControl.md)|建立在 MFC 容器的 Windows Form 控制項。|  
|[CWinFormsControl::GetControl](../Topic/CWinFormsControl::GetControl.md)|擷取指標對 Windows Form 控制項。|  
|[CWinFormsControl::GetControlHandle](../Topic/CWinFormsControl::GetControlHandle.md)|擷取控制代碼為 Windows Form 控制項。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CWinFormsControl::operator \-\>](../Topic/CWinFormsControl::operator%20-%3E.md)|在取代運算式中 [CWinFormsControl::GetControl](../Topic/CWinFormsControl::GetControl.md) 。|  
|[CWinFormsControl::operator TManagedControl^](../Topic/CWinFormsControl::operator%20TManagedControl%5E.md)|轉換為型別為指標對 Windows Form 控制項。|  
  
## 備註  
 `CWinFormsControl` 類別來裝載 Windows Form 控制項的基本功能。  
  
 如需使用 Windows Form 的詳細資訊，請參閱 [在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。  
  
 您的 MFC 程式碼不應該快取視窗控制代碼 \(通常是儲存在 `m_hWnd`\)。  有些 Windows Form 控制項屬性需要使用 `DestroyWindow` 和 `CreateWindow`，基礎 Win32 `Window` 終結然後再重新建立。  MFC Windows Form 實作處理控制項的和事件 `Destroy``Create` 更新 `m_hWnd` 成員。  
  
> [!NOTE]
>  MFC Windows Form 整合只有在和 MFC 動態連結的專案中才有作用 \(有定義 AFXDLL 的\)。  
  
## 需求  
 **標題:** afxwinforms.h  
  
## 請參閱  
 [CWinFormsDialog Class](../../mfc/reference/cwinformsdialog-class.md)   
 [CWinFormsView Class](../../mfc/reference/cwinformsview-class.md)