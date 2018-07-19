---
title: CMFCRibbonButtonsGroup 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonButtonsGroup
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::AddButton
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::AddButtons
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetButton
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetCount
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetImageSize
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetRegularSize
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::HasImages
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::OnDrawImage
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::RemoveAll
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::SetImages
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::SetParentCategory
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonButtonsGroup [MFC], CMFCRibbonButtonsGroup
- CMFCRibbonButtonsGroup [MFC], AddButton
- CMFCRibbonButtonsGroup [MFC], AddButtons
- CMFCRibbonButtonsGroup [MFC], GetButton
- CMFCRibbonButtonsGroup [MFC], GetCount
- CMFCRibbonButtonsGroup [MFC], GetImageSize
- CMFCRibbonButtonsGroup [MFC], GetRegularSize
- CMFCRibbonButtonsGroup [MFC], HasImages
- CMFCRibbonButtonsGroup [MFC], OnDrawImage
- CMFCRibbonButtonsGroup [MFC], RemoveAll
- CMFCRibbonButtonsGroup [MFC], SetImages
- CMFCRibbonButtonsGroup [MFC], SetParentCategory
ms.assetid: b993d93e-fc1a-472f-a87f-1d7b7b499845
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 855bc48da10e8ca4dd83cf091e155746450a33f1
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/05/2018
ms.locfileid: "37848515"
---
# <a name="cmfcribbonbuttonsgroup-class"></a>CMFCRibbonButtonsGroup 類別
`CMFCRibbonButtonsGroup`類別可讓您將一組功能區按鈕組織成群組。 群組中的所有按鈕彼此水平直接相鄰，而且以框線框住。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCRibbonButtonsGroup : public CMFCRibbonBaseElement  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup](#cmfcribbonbuttonsgroup)|建構 `CMFCRibbonButtonsGroup` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCRibbonButtonsGroup::AddButton](#addbutton)|將按鈕加入到群組。|  
|[CMFCRibbonButtonsGroup::AddButtons](#addbuttons)|將按鈕的清單加入至群組。|  
|[CMFCRibbonButtonsGroup::GetButton](#getbutton)|讓指標回到指定的索引處的按鈕。|  
|[CMFCRibbonButtonsGroup::GetCount](#getcount)|傳回群組中的按鈕數目。|  
|[CMFCRibbonButtonsGroup::GetImageSize](#getimagesize)|傳回功能區群組中的一般的映像的映像大小 (會覆寫[cmfcribbonbaseelement:: Getimagesize](../../mfc/reference/cmfcribbonbaseelement-class.md#getimagesize)。)|  
|[CMFCRibbonButtonsGroup::GetRegularSize](#getregularsize)|傳回功能區項目的一般大小 (會覆寫[cmfcribbonbaseelement:: Getregularsize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize)。)|  
|[CMFCRibbonButtonsGroup::HasImages](#hasimages)|報告是否`CMFCRibbonButtonsGroup`物件包含工具列影像。|  
|[CMFCRibbonButtonsGroup::OnDrawImage](#ondrawimage)|繪製指定的按鈕，根據按鈕是否正常、 反白顯示或停用適當的映像。|  
|[CMFCRibbonButtonsGroup::RemoveAll](#removeall)|移除所有的按鈕，從`CMFCRibbonButtonsGroup`物件。|  
|[CMFCRibbonButtonsGroup::SetImages](#setimages)|將映像指派給群組。|  
|[CMFCRibbonButtonsGroup::SetParentCategory](#setparentcategory)|設定父系`CMFCRibbonCategory`的`CMFCRibbonButtonsGroup`物件和其內的所有按鈕 (會覆寫[cmfcribbonbaseelement:: Setparentcategory](../../mfc/reference/cmfcribbonbaseelement-class.md#setparentcategory)。)|  
  
## <a name="remarks"></a>備註  
 群組衍生自[CMFCBaseRibbonElement](../../mfc/reference/cmfcribbonbaseelement-class.md)也可以當做單一實體進行操作。 您可以在任何面板或快顯功能表放置群組。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用中的各種方法`CMFCRibbonButtonsGroup`類別。 此範例示範如何建構`CMFCRibbonButtonsGroup`物件、 將映像指派給功能區按鈕群組，並將按鈕加入的功能區按鈕的群組。 這段程式碼片段是 [Draw 用戶端範例](../../visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_DrawClient#2](../../mfc/reference/codesnippet/cpp/cmfcribbonbuttonsgroup-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButtonsGroup](../../mfc/reference/cmfcribbonbuttonsgroup-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxribbonbuttonsgroup.h  
  
##  <a name="addbutton"></a>  CMFCRibbonButtonsGroup::AddButton  
 將按鈕加入到群組。  
  
```  
void AddButton(CMFCRibbonBaseElement* pButton);
```  
  
### <a name="parameters"></a>參數  
 [in]*pButton*  
 按鈕以新增指標。  
  
##  <a name="addbuttons"></a>  CMFCRibbonButtonsGroup::AddButtons  
 將按鈕的清單加入至群組。  
  
```  
void AddButtons(
    const CList<CMFCRibbonBaseElement*,CMFCRibbonBaseElement*>& lstButtons);
```  
  
### <a name="parameters"></a>參數  
 [in]*lstButtons*  
 您想要新增的按鈕指標的清單。  
  
##  <a name="cmfcribbonbuttonsgroup"></a>  CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup  
 建構 `CMFCRibbonButtonsGroup` 物件。  
  
```  
CMFCRibbonButtonsGroup();
CMFCRibbonButtonsGroup(CMFCRibbonBaseElement* pButton);
```  
  
### <a name="parameters"></a>參數  
 [in]*pButton*  
 指定將新增至新建立的按鈕`CMFCRibbonButtonsGroup`物件。  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="getbutton"></a>  CMFCRibbonButtonsGroup::GetButton  
 讓指標回到指定的索引處的按鈕。  
  
```  
CMFCRibbonBaseElement* GetButton(int i) const;  
```  
  
### <a name="parameters"></a>參數  
 [in]*我*  
 按鈕，以傳回以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 指標，位於指定索引處的按鈕。 如果指定的索引超出範圍，則為 NULL。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getcount"></a>  CMFCRibbonButtonsGroup::GetCount  
 傳回群組中的按鈕數目。  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 在群組中的按鈕數目。  
  
##  <a name="getimagesize"></a>  CMFCRibbonButtonsGroup::GetImageSize  
 擷取受保護的來源映像大小`CMFCToolBarImages`成員`m_Images`。  
  
```  
const CSize GetImageSize() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果有的話，或傳回工具列影像的來源映像大小`CSize`為零，如果不是。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getregularsize"></a>  CMFCRibbonButtonsGroup::GetRegularSize  
 擷取功能區群組元素的最大可能大小。  
  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [in]*pDC*  
 功能區群組的裝置內容指標。  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="hasimages"></a>  CMFCRibbonButtonsGroup::HasImages  
 報告是否`CMFCRibbonButtonsGroup`物件包含工具列影像。  
  
```  
BOOL HasImages() const;  
```  
  
### <a name="return-value"></a>傳回值  
 會傳回 TRUE，如果受保護`CMFCToolBarImages`成員`m_Images`不包含任何映像或 false。  
  
### <a name="remarks"></a>備註  
  
##  <a name="ondrawimage"></a>  CMFCRibbonButtonsGroup::OnDrawImage  
 繪製指定的按鈕，根據按鈕是否正常、 反白顯示或停用適當的映像。  
  
```  
virtual void OnDrawImage(
    CDC* pDC,  
    CRect rectImage,  
    CMFCRibbonBaseElement* pButton,  
    int nImageIndex);
```  
  
### <a name="parameters"></a>參數  
 [in]*pDC*  
 裝置內容指標`CMFCRibbonButtonsGroup`物件。  
  
 [in]*rectImage*  
 在其中繪製影像的矩形。  
  
 [in]*pButton*  
 要繪製影像按鈕。  
  
 [in]*nImageIndex*  
 （在三個映像陣列以進行一般、 反白顯示或停用按鈕） 的按鈕上繪製影像的索引。  
  
### <a name="remarks"></a>備註  
  
##  <a name="removeall"></a>  CMFCRibbonButtonsGroup::RemoveAll  
 移除所有的按鈕，從`CMFCRibbonButtonsGroup`物件。  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="setimages"></a>  CMFCRibbonButtonsGroup::SetImages  
 將映像指派給功能區按鈕群組中。  
  
```  
void SetImages(
    CMFCToolBarImages* pImages,  
    CMFCToolBarImages* pHotImages,  
    CMFCToolBarImages* pDisabledImages);
```  
  
### <a name="parameters"></a>參數  
 [in]*pImages*  
 一般的映像。  
  
 [in]*pHotImages*  
 最忙碌的映像。  
  
 [in]*pDisabledImages*  
 已停用的映像。  
  
### <a name="remarks"></a>備註  
 呼叫`SetImages`按鈕新增至群組之前。 映像數目必須大於或等於要新增至群組的按鈕數目。  
  
> [!NOTE]
>  作用中影像是當使用者將滑鼠指標停留在按鈕上時所顯示的映像。 已停用的影像是按鈕已停用時所顯示的映像。  
  
##  <a name="setparentcategory"></a>  CMFCRibbonButtonsGroup::SetParentCategory  
 設定父系`CMFCRibbonCategory`的`CMFCRibbonButtonsGroup`物件和其內的所有按鈕。  
  
```  
virtual void SetParentCategory(CMFCRibbonCategory* pCategory);
```  
  
### <a name="parameters"></a>參數  
 [in]*pCategory*  
 父類別，來設定指標 （在功能區控制項的索引標籤式的群組稱為類別）。  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)
