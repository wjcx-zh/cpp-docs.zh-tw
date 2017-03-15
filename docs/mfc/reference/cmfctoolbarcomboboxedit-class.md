---
title: "CMFCToolBarComboBoxEdit 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCComboEdit
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarComboBoxEdit class
- CMFCToolBarComboBoxEdit::PreTranslateMessage method
ms.assetid: 4789c34a-ce58-48ba-a26f-38748b601352
caps.latest.revision: 25
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 3c0f2ade3292fb238a227e881951604606baec79
ms.lasthandoff: 02/24/2017

---
# <a name="cmfctoolbarcomboboxedit-class"></a>CMFCToolBarComboBoxEdit 類別
架構會使用`CMFCToolBarComboBoxEdit`類別來建立行為類似的可編輯的下拉式方塊控制項的工具列按鈕。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCToolBarComboBoxEdit : public CEdit  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCToolBarComboBoxEdit::CMFCToolBarComboBoxEdit](#cmfctoolbarcomboboxedit)|建構 `CMFCToolBarComboBoxEdit` 物件。|  
|`CMFCToolBarComboBoxEdit::~CMFCToolBarComboBoxEdit`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|`CMFCToolBarComboBoxEdit::PreTranslateMessage`|轉譯的視窗訊息，再分派給[TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955)和[DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函式。 (覆寫[CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。)|  
  
### <a name="remarks"></a>備註  
 自`CMFCToolBarComboBoxEdit`類別來自訂其編輯作業。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CEdit](../../mfc/reference/cedit-class.md)  
  
 [CMFCToolBarComboBoxEdit](../../mfc/reference/cmfctoolbarcomboboxedit-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxtoolbarcomboboxbutton.h  
  
##  <a name="a-namecmfctoolbarcomboboxedita--cmfctoolbarcomboboxeditcmfctoolbarcomboboxedit"></a><a name="cmfctoolbarcomboboxedit"></a>CMFCToolBarComboBoxEdit::CMFCToolBarComboBoxEdit  
 建構 `CMFCToolBarComboBoxEdit` 物件。  
  
```  
CMFCToolBarComboBoxEdit(CMFCToolBarComboBoxButton& combo);
```  
  
### <a name="parameters"></a>參數  
 [in] `combo`  
 參考[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)物件，這是包含下拉式方塊控制項的工具列按鈕。  
  
### <a name="example"></a>範例  
 下列範例示範如何建構的物件`CMFCToolBarComboBoxEdit`類別。 此程式碼片段是一部分[IE 示範範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_IEDemo #&5;](../../mfc/reference/codesnippet/cpp/cmfctoolbarcomboboxedit-class_1.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarComboBoxButton 類別](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

