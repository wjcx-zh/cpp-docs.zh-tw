---
title: "CMFCDesktopAlertWndButton 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCDesktopAlertWndButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton::IsCaptionButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton::IsCloseButton
dev_langs: C++
helpviewer_keywords:
- CMFCDesktopAlertWndButton [MFC], IsCaptionButton
- CMFCDesktopAlertWndButton [MFC], IsCloseButton
ms.assetid: df39a0c8-0c39-4ab0-8c64-78c5b2c4ecaf
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ae1153546851e6a34c14dacd33db04091de24557
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcdesktopalertwndbutton-class"></a>CMFCDesktopAlertWndButton 類別
可讓要新增至桌面的警示對話方塊的按鈕。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCDesktopAlertWndButton : public CMFCButton  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|||  
|-|-|  
|名稱|描述|  
|`CMFCDesktopAlertWndButton::CMFCDesktopAlertWndButton`|預設建構函式。|  
|`CMFCDesktopAlertWndButton::~CMFCDesktopAlertWndButton`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|||  
|-|-|  
|名稱|描述|  
|[CMFCDesktopAlertWndButton::IsCaptionButton](#iscaptionbutton)|決定是否要將按鈕顯示 [警示] 對話方塊的標題區域中。|  
|[CMFCDesktopAlertWndButton::IsCloseButton](#isclosebutton)|決定按鈕是否要關閉警示 對話方塊。|  
  
### <a name="data-members"></a>資料成員  
  
|||  
|-|-|  
|名稱|描述|  
|`CMFCDesktopAlertWndButton::m_bIsCaptionButton`|布林值，指定是否要將按鈕顯示 [警示] 對話方塊的標題區域中。|  
|`CMFCDesktopAlertWndButton::m_bIsCloseButton`|布林值，指定按鈕是否要關閉警示 對話方塊。|  
  
### <a name="remarks"></a>備註  
 根據預設，建構函式設定`m_bIsCaptionButton`和`m_bIsCloseButton`資料成員`FALSE`。 父代`CMFCDesktopAlertDialog`物件集`m_bIsCaptionButton`至`TRUE`如果按鈕位於 [警示] 對話方塊的標題區域中。 `CMFCDesktopAlertDialog`類別會建立`CMFCDesktopAlertWndButton`物件，可做為關閉警示 對話方塊的按鈕方塊，並設定`m_bIsCloseButton`至`TRUE`。  
  
 新增`CMFCDesktopAlertWndButton`物件加入至`CMFCDesktopAlertDialog`物件與加入的任何按鈕。 如需有關`CMFCDesktopAlertDialog`，請參閱[CMFCDesktopAlertDialog 類別](../../mfc/reference/cmfcdesktopalertdialog-class.md)。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用`SetImage`方法中的`CMFCDesktopAlertWndButton`類別。 此程式碼片段是部分[桌面警示示範範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_DesktopAlertDemo#4](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndbutton-class_1.h)]  
[!code-cpp[NVC_MFC_DesktopAlertDemo#5](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndbutton-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCButton](../../mfc/reference/cmfcbutton-class.md)  
  
 [CMFCDesktopAlertWndButton](../../mfc/reference/cmfcdesktopalertwndbutton-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxdesktopalertwnd.h  
  
##  <a name="iscaptionbutton"></a>CMFCDesktopAlertWndButton::IsCaptionButton  
 決定是否要將按鈕顯示 [警示] 對話方塊的標題區域中。  
  
```  
BOOL IsCaptionButton() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果按鈕會顯示在標題區域的 [警示] 對話方塊中，則為非零否則為 0。  
  
##  <a name="isclosebutton"></a>CMFCDesktopAlertWndButton::IsCloseButton  
 決定按鈕是否要關閉警示 對話方塊。  
  
```  
BOOL IsCloseButton() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果按鈕關閉 [警示] 對話方塊中，則為非零否則為 0。  
  
## <a name="see-also"></a>請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCDesktopAlertDialog 類別](../../mfc/reference/cmfcdesktopalertdialog-class.md)
