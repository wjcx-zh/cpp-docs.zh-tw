---
title: "CMFCToolBarFontSizeComboBox 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
- CMFCToolBarFontSizeComboBox class
ms.assetid: 72e0c44c-6a0e-4194-a71f-ab64e3afb9b5
caps.latest.revision: 26
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
ms.openlocfilehash: 9dddb563617a708bdc8b2193fa5ee8bd10321828
ms.lasthandoff: 02/24/2017

---
# <a name="cmfctoolbarfontsizecombobox-class"></a>CMFCToolBarFontSizeComboBox 類別
工具列按鈕，其中包含可讓使用者選取字型大小的下拉式方塊控制項。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCToolBarFontSizeComboBox : public CMFCToolBarComboBoxButton  
```  
  
## <a name="members"></a>Members  
  
### <a name="protected-constructors"></a>受保護的建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox](#cmfctoolbarfontsizecombobox)|建構 `CMFCToolBarFontSizeComboBox` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCToolBarFontSizeComboBox::GetTwipSize](#gettwipsize)|傳回所選的字型大小二分之一為單位。|  
|[CMFCToolBarFontSizeComboBox::RebuildFontSizes](#rebuildfontsizes)|所有支援的字型大小指定字型中填入下拉式方塊的清單。|  
|[CMFCToolBarFontSizeComboBox::SetTwipSize](#settwipsize)|將字型大小設定二分之一為單位。|  
  
## <a name="remarks"></a>備註  
 您可以使用`CMFCToolBarFontSizeComboBox`物件搭配[CMFCToolBarFontComboBox 類別](../../mfc/reference/cmfctoolbarfontcombobox-class.md)物件，讓使用者選取字型與大小。  
  
 就像您加入字型下拉式方塊按鈕，您可以加入工具列的字型下拉式方塊按鈕。 如需詳細資訊，請參閱[CMFCToolBarFontComboBox 類別](../../mfc/reference/cmfctoolbarfontcombobox-class.md)。  
  
 當使用者選取新字型`CMFCToolBarFontComboBox`物件時，您也可以使用該字型支援的大小與填入字型大小下拉式方塊[CMFCToolBarFontSizeComboBox::RebuildFontSizes](#rebuildfontsizes)方法。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用各種方法的`CMFCToolBarFontSizeComboBox`類別來設定`CMFCToolBarFontSizeComboBox`物件。 此範例說明如何擷取字型大小二分之一，在文字方塊中，填入所有有效的大小，指定字型的字型的大小下拉式方塊和二分之一為單位指定的字型大小。 此程式碼片段是一部分[字板範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_WordPad #&8;](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontsizecombobox-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)  
  
 [CMFCToolBarFontSizeComboBox](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxtoolbarfontcombobox.h  
  
##  <a name="cmfctoolbarfontsizecombobox"></a>CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox  
 建構 `CMFCToolBarFontSizeComboBox` 物件。  
  
```  
CMFCToolBarFontSizeComboBox();
```  
  
##  <a name="gettwipsize"></a>CMFCToolBarFontSizeComboBox::GetTwipSize  
 擷取文字大小二分之一，字型大小下拉式方塊的文字方塊中。  
  
```  
int GetTwipSize() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果傳回值是正數，則二分之一文字大小。 如果下拉式方塊的文字方塊為空白，則為-1。 如果發生錯誤時，它可以是-2。  
  
##  <a name="rebuildfontsizes"></a>CMFCToolBarFontSizeComboBox::RebuildFontSizes  
 填入所有有效的大小，指定字型的字型大小下拉式方塊。  
  
```  
void RebuildFontSizes(const CString& strFontName);
```  
  
### <a name="parameters"></a>參數  
 `[in] strFontName`  
 指定的字型名稱。  
  
### <a name="remarks"></a>備註  
 呼叫此函式，當您要同步處理一個字型下拉式方塊中的選取項目與字型大小下拉式方塊中，例如[CMFCToolBarFontComboBox 類別](../../mfc/reference/cmfctoolbarfontcombobox-class.md)。  
  
##  <a name="settwipsize"></a>CMFCToolBarFontSizeComboBox::SetTwipSize  
 將指定大小 （以二分之一） 的最接近的大小，以點，然後集值的下拉式方塊中選取的大小。  
  
```  
void SetTwipSize(int nSize);
```  
  
### <a name="parameters"></a>參數  
 [in] `nSize`  
 指定的字型大小 （以二分之一） 來設定。  
  
### <a name="remarks"></a>備註  
 您可以稍後擷取前一個有效的字型大小，藉由呼叫[CMFCToolBarFontSizeComboBox::GetTwipSize](#gettwipsize)方法。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [CMFCToolBarComboBoxButton 類別](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)   
 [CMFCFontInfo 類別](../../mfc/reference/cmfcfontinfo-class.md)   
 [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)   
 [逐步解說︰ 將放在工具列上的控制項](../../mfc/walkthrough-putting-controls-on-toolbars.md)




