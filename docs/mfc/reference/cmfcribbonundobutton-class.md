---
title: CMFCRibbonUndoButton 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::AddUndoAction
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::CleanUpUndoList
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::GetActionNumber
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::HasMenu
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonUndoButton [MFC], CMFCRibbonUndoButton
- CMFCRibbonUndoButton [MFC], AddUndoAction
- CMFCRibbonUndoButton [MFC], CleanUpUndoList
- CMFCRibbonUndoButton [MFC], GetActionNumber
- CMFCRibbonUndoButton [MFC], HasMenu
ms.assetid: 5c42adf7-871d-4239-901e-47ae7fb816fc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 233f37fc0ab31afcd8ba112677af8cd144d01c2a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33370164"
---
# <a name="cmfcribbonundobutton-class"></a>CMFCRibbonUndoButton 類別
`CMFCRibbonUndoButton`類別實作，其中包含最新的使用者命令中的下拉式清單按鈕。 使用者可以從要取消復原或復原這些下拉式清單中選取一或多個最新的命令。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCRibbonUndoButton : public CMFCRibbonGallery  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCRibbonUndoButton::CMFCRibbonUndoButton](#cmfcribbonundobutton)|建構新`CMFCRibbonUndoButton`使用您指定的命令識別碼、 文字標籤和映像從影像清單的父物件的物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCRibbonUndoButton::AddUndoAction](#addundoaction)|將新的動作加入至動作的清單。|  
|[CMFCRibbonUndoButton::CleanUpUndoList](#cleanupundolist)|清除動作清單，這是下拉式清單。|  
|[CMFCRibbonUndoButton::GetActionNumber](#getactionnumber)|決定使用者從下拉式清單中選取的項目數目。|  
|[CMFCRibbonUndoButton::HasMenu](#hasmenu)|指出物件是否包含功能表。|  
  
## <a name="remarks"></a>備註  
 `CMFCRibbonUndoButton`類別來代表下拉式清單使用的堆疊。  
  
## <a name="example"></a>範例  
 下列範例示範如何建構的物件`CMFCRibbonUndoButton`類別，並加入新的動作的動作清單。 此程式碼片段是部分[功能區小工具範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_RibbonGadgets#2](../../mfc/reference/codesnippet/cpp/cmfcribbonundobutton-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)  
  
 [CMFCRibbonUndoButton](../../mfc/reference/cmfcribbonundobutton-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxribbonundobutton.h  
  
##  <a name="addundoaction"></a>  CMFCRibbonUndoButton::AddUndoAction  
 將新的動作加入至動作的清單。  
  
```  
void AddUndoAction(LPCTSTR lpszLabel);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `lpszLabel`  
 將會顯示在下拉式清單中的動作標籤。  
  
##  <a name="cleanupundolist"></a>  CMFCRibbonUndoButton::CleanUpUndoList  
 清除動作清單，這是下拉式清單。  
  
```  
void CleanUpUndoList();
```  
  
##  <a name="cmfcribbonundobutton"></a>  CMFCRibbonUndoButton::CMFCRibbonUndoButton  
 建構新`CMFCRibbonUndoButton`使用您指定的命令識別碼、 文字標籤和映像從影像清單的父物件的物件。  
  
```  
CMFCRibbonUndoButton(
    UINT nID,  
    LPCTSTR lpszText,  
    int nSmallImageIndex=-1,  
    int nLargeImageIndex=-1);

 
CMFCRibbonUndoButton(
    UINT nID,  
    LPCTSTR lpszText,  
    HICON hIcon);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `nID`  
 指定命令識別碼。  
  
 [輸入] `lpszText`  
 指定按鈕的文字標籤。  
  
 [輸入] `nSmallImageIndex`  
 按鈕的小型影像的父物件的影像清單中以零為起始的索引。  
  
 [輸入] `nLargeImageIndex`  
 以零為起始的索引的父物件的影像清單中的按鈕的大型影像。  
  
 [輸入] `hIcon`  
 您可以使用做為按鈕的影像圖示的控制代碼。  
  
##  <a name="getactionnumber"></a>  CMFCRibbonUndoButton::GetActionNumber  
 決定使用者從下拉式清單中選取的項目數目。  
  
```  
int GetActionNumber() const;  
```  
  
### <a name="return-value"></a>傳回值  
 使用者選取的項目數目。  
  
##  <a name="hasmenu"></a>  CMFCRibbonUndoButton::HasMenu  
 指出物件是否包含功能表。  
  
```  
virtual BOOL HasMenu() const;  
```  
  
### <a name="return-value"></a>傳回值  
 一律傳回 `TRUE`。  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonGallery 類別](../../mfc/reference/cmfcribbongallery-class.md)   
 [CMFCRibbonButton 類別](../../mfc/reference/cmfcribbonbutton-class.md)
