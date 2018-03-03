---
title: "CMFCToolBarComboBoxEdit 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCToolBarComboBoxEdit
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxEdit
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxEdit::CMFCToolBarComboBoxEdit
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarComboBoxEdit [MFC], CMFCToolBarComboBoxEdit
ms.assetid: 4789c34a-ce58-48ba-a26f-38748b601352
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7d7e83351c9adbf7730fad04f2e4d73431694f3c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cmfctoolbarcomboboxedit-class"></a>CMFCToolBarComboBoxEdit 類別
架構會使用`CMFCToolBarComboBoxEdit`類別來建立行為類似的可編輯的下拉式方塊控制項的工具列按鈕。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCToolBarComboBoxEdit : public CEdit  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCToolBarComboBoxEdit::CMFCToolBarComboBoxEdit](#cmfctoolbarcomboboxedit)|建構 `CMFCToolBarComboBoxEdit` 物件。|  
|`CMFCToolBarComboBoxEdit::~CMFCToolBarComboBoxEdit`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|`CMFCToolBarComboBoxEdit::PreTranslateMessage`|將視窗訊息轉譯分派至之前[TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955)和[DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函式。 (覆寫 [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。)|  
  
### <a name="remarks"></a>備註  
 自`CMFCToolBarComboBoxEdit`類別來自訂其編輯作業。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CEdit](../../mfc/reference/cedit-class.md)  
  
 [CMFCToolBarComboBoxEdit](../../mfc/reference/cmfctoolbarcomboboxedit-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxtoolbarcomboboxbutton.h  
  
##  <a name="cmfctoolbarcomboboxedit"></a>CMFCToolBarComboBoxEdit::CMFCToolBarComboBoxEdit  
 建構 `CMFCToolBarComboBoxEdit` 物件。  
  
```  
CMFCToolBarComboBoxEdit(CMFCToolBarComboBoxButton& combo);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `combo`  
 若要參考[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)物件，它是包含下拉式方塊控制項的工具列按鈕。  
  
### <a name="example"></a>範例  
 下列範例示範如何建構的物件`CMFCToolBarComboBoxEdit`類別。 此程式碼片段是部分[IE 示範範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_IEDemo#5](../../mfc/reference/codesnippet/cpp/cmfctoolbarcomboboxedit-class_1.cpp)]  
  
## <a name="see-also"></a>請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarComboBoxButton 類別](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)
