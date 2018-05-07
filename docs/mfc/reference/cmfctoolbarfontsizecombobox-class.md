---
title: CMFCToolBarFontSizeComboBox 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::GetTwipSize
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::RebuildFontSizes
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::SetTwipSize
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarFontSizeComboBox [MFC], CMFCToolBarFontSizeComboBox
- CMFCToolBarFontSizeComboBox [MFC], GetTwipSize
- CMFCToolBarFontSizeComboBox [MFC], RebuildFontSizes
- CMFCToolBarFontSizeComboBox [MFC], SetTwipSize
ms.assetid: 72e0c44c-6a0e-4194-a71f-ab64e3afb9b5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4b2c5734618bf1bedc72fe78dbeaada8c437391f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cmfctoolbarfontsizecombobox-class"></a>CMFCToolBarFontSizeComboBox 類別
包含可讓使用者選取字型的大小的下拉式方塊控制項的工具列按鈕。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCToolBarFontSizeComboBox : public CMFCToolBarComboBoxButton  
```  
  
## <a name="members"></a>成員  
  
### <a name="protected-constructors"></a>受保護的建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox](#cmfctoolbarfontsizecombobox)|建構 `CMFCToolBarFontSizeComboBox` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCToolBarFontSizeComboBox::GetTwipSize](#gettwipsize)|傳回所選的字型大小，以 twip 為單位。|  
|[CMFCToolBarFontSizeComboBox::RebuildFontSizes](#rebuildfontsizes)|填入指定字型的所有字型支援的大小下拉式方塊的清單。|  
|[CMFCToolBarFontSizeComboBox::SetTwipSize](#settwipsize)|設定字型大小，以 twip 為單位。|  
  
## <a name="remarks"></a>備註  
 您可以使用`CMFCToolBarFontSizeComboBox`物件搭配[CMFCToolBarFontComboBox 類別](../../mfc/reference/cmfctoolbarfontcombobox-class.md)物件，讓使用者選取字型與大小。  
  
 就如同您將字型下拉式方塊按鈕加入您可以加入工具列的字型下拉式方塊按鈕。 如需詳細資訊，請參閱[CMFCToolBarFontComboBox 類別](../../mfc/reference/cmfctoolbarfontcombobox-class.md)。  
  
 當使用者選取中的新字型`CMFCToolBarFontComboBox`物件，您也可以使用該字型支援的大小與填入字型大小下拉式方塊[CMFCToolBarFontSizeComboBox::RebuildFontSizes](#rebuildfontsizes)方法。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用各種方法的`CMFCToolBarFontSizeComboBox`用來設定類別`CMFCToolBarFontSizeComboBox`物件。 此範例說明如何擷取字型大小，以 twip 為單位，從文字方塊、 填入所有有效的大小，指定字型的字型大小下拉式方塊和指定的字型大小，以 twip 為單位。 此程式碼片段是 [WordPad 範例](../../visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_WordPad#8](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontsizecombobox-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)  
  
 [CMFCToolBarFontSizeComboBox](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxtoolbarfontcombobox.h  
  
##  <a name="cmfctoolbarfontsizecombobox"></a>  CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox  
 建構 `CMFCToolBarFontSizeComboBox` 物件。  
  
```  
CMFCToolBarFontSizeComboBox();
```  
  
##  <a name="gettwipsize"></a>  CMFCToolBarFontSizeComboBox::GetTwipSize  
 文字大小，以 twip 為單位，擷取的字型大小 下拉式方塊的文字方塊。  
  
```  
int GetTwipSize() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果傳回值是正數，是以 twip 為單位的字型大小。 如果下拉式方塊的文字方塊是空的它會為-1。 如果發生錯誤，它會為-2。  
  
##  <a name="rebuildfontsizes"></a>  CMFCToolBarFontSizeComboBox::RebuildFontSizes  
 字型的大小下拉式方塊中填入指定字型的所有有效的大小。  
  
```  
void RebuildFontSizes(const CString& strFontName);
```  
  
### <a name="parameters"></a>參數  
 `[in] strFontName`  
 指定的字型名稱。  
  
### <a name="remarks"></a>備註  
 呼叫此函式，當您想要同步字型下拉式方塊中的選取項目字型的大小下拉式方塊中，處理這類[CMFCToolBarFontComboBox 類別](../../mfc/reference/cmfctoolbarfontcombobox-class.md)。  
  
##  <a name="settwipsize"></a>  CMFCToolBarFontSizeComboBox::SetTwipSize  
 回合中指定的大小 （以 twip 為單位） 的最接近的大小，以點，然後設定該值的下拉式方塊中選取的大小。  
  
```  
void SetTwipSize(int nSize);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `nSize`  
 若要設定指定的字型大小 （以 twip 為單位）。  
  
### <a name="remarks"></a>備註  
 您可以稍後擷取先前有效的字型的大小，藉由呼叫[CMFCToolBarFontSizeComboBox::GetTwipSize](#gettwipsize)方法。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [CMFCToolBarComboBoxButton 類別](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)   
 [CMFCFontInfo 類別](../../mfc/reference/cmfcfontinfo-class.md)   
 [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)   
 [逐步解說：將控制項放在工具列上](../../mfc/walkthrough-putting-controls-on-toolbars.md)



