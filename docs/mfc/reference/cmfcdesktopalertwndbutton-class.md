---
title: "CMFCDesktopAlertWndButton 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCDesktopAlertWndButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton::IsCaptionButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton::IsCloseButton
dev_langs:
- C++
helpviewer_keywords:
- CMFCDesktopAlertWndButton class
ms.assetid: df39a0c8-0c39-4ab0-8c64-78c5b2c4ecaf
caps.latest.revision: 23
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 52294143c6caf5a8e0458c152540c41f7df78c57
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcdesktopalertwndbutton-class"></a>CMFCDesktopAlertWndButton 類別
允許加入桌面警示對話方塊的按鈕。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCDesktopAlertWndButton : public CMFCButton  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|||  
|-|-|  
|名稱|說明|  
|`CMFCDesktopAlertWndButton::CMFCDesktopAlertWndButton`|預設建構函式。|  
|`CMFCDesktopAlertWndButton::~CMFCDesktopAlertWndButton`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|||  
|-|-|  
|名稱|說明|  
|[CMFCDesktopAlertWndButton::IsCaptionButton](#iscaptionbutton)|決定是否要將按鈕顯示 [警示] 對話方塊的標題區域中。|  
|[CMFCDesktopAlertWndButton::IsCloseButton](#isclosebutton)|決定按鈕是否要關閉警示 對話方塊。|  
  
### <a name="data-members"></a>資料成員  
  
|||  
|-|-|  
|名稱|說明|  
|`CMFCDesktopAlertWndButton::m_bIsCaptionButton`|布林值，指定是否要將按鈕顯示 [警示] 對話方塊的標題區域中。|  
|`CMFCDesktopAlertWndButton::m_bIsCloseButton`|布林值，指定按鈕是否要關閉警示 對話方塊。|  
  
### <a name="remarks"></a>備註  
 根據預設，建構函式設定`m_bIsCaptionButton`和`m_bIsCloseButton`資料成員`FALSE`。 父代`CMFCDesktopAlertDialog`物件集`m_bIsCaptionButton`至`TRUE`如果按鈕位於 [警示] 對話方塊的標題區域中。 `CMFCDesktopAlertDialog`類別會建立`CMFCDesktopAlertWndButton`物件，可做為關閉警示 對話方塊的按鈕方塊，並設定`m_bIsCloseButton`到`TRUE`。  
  
 新增`CMFCDesktopAlertWndButton`物件加入至`CMFCDesktopAlertDialog`物件，您可以加入任何按鈕。 如需詳細資訊`CMFCDesktopAlertDialog`，請參閱[CMFCDesktopAlertDialog 類別](../../mfc/reference/cmfcdesktopalertdialog-class.md)。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用`SetImage`方法中的`CMFCDesktopAlertWndButton`類別。 此程式碼片段是一部分[桌面警示示範範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_DesktopAlertDemo #&4;](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndbutton-class_1.h)]  
[!code-cpp[NVC_MFC_DesktopAlertDemo #&5;](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndbutton-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCButton](../../mfc/reference/cmfcbutton-class.md)  
  
 [CMFCDesktopAlertWndButton](../../mfc/reference/cmfcdesktopalertwndbutton-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxdesktopalertwnd.h  
  
##  <a name="iscaptionbutton"></a>CMFCDesktopAlertWndButton::IsCaptionButton  
 決定是否要將按鈕顯示 [警示] 對話方塊的標題區域中。  
  
```  
BOOL IsCaptionButton() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果按鈕會顯示在標題區域的 [警示] 對話方塊中，為非零否則為 0。  
  
##  <a name="isclosebutton"></a>CMFCDesktopAlertWndButton::IsCloseButton  
 決定按鈕是否要關閉警示 對話方塊。  
  
```  
BOOL IsCloseButton() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果按鈕會關閉警示 對話方塊中，為非零否則為 0。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCDesktopAlertDialog 類別](../../mfc/reference/cmfcdesktopalertdialog-class.md)

