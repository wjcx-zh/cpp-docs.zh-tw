---
title: "CMFCRibbonComboBox 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::CMFCRibbonComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::AddItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::DeleteItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::EnableDropDownListResize
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::FindItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetCount
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetCurSel
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetDropDownHeight
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetIntermediateSize
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetItemData
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::HasEditBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::IsResizeDropDownList
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::OnSelectItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::RemoveAllItems
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::SelectItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::SetDropDownHeight
dev_langs: C++
helpviewer_keywords:
- CMFCRibbonComboBox [MFC], CMFCRibbonComboBox
- CMFCRibbonComboBox [MFC], AddItem
- CMFCRibbonComboBox [MFC], DeleteItem
- CMFCRibbonComboBox [MFC], EnableDropDownListResize
- CMFCRibbonComboBox [MFC], FindItem
- CMFCRibbonComboBox [MFC], GetCount
- CMFCRibbonComboBox [MFC], GetCurSel
- CMFCRibbonComboBox [MFC], GetDropDownHeight
- CMFCRibbonComboBox [MFC], GetIntermediateSize
- CMFCRibbonComboBox [MFC], GetItem
- CMFCRibbonComboBox [MFC], GetItemData
- CMFCRibbonComboBox [MFC], HasEditBox
- CMFCRibbonComboBox [MFC], IsResizeDropDownList
- CMFCRibbonComboBox [MFC], OnSelectItem
- CMFCRibbonComboBox [MFC], RemoveAllItems
- CMFCRibbonComboBox [MFC], SelectItem
- CMFCRibbonComboBox [MFC], SetDropDownHeight
ms.assetid: 9b29a6a4-cf17-4152-9b13-0bf90784b30d
caps.latest.revision: "35"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 921be1bdcebfabbcca8e07cefc2ee9a0b40f84f0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="cmfcribboncombobox-class"></a>CMFCRibbonComboBox 類別
`CMFCRibbonComboBox`類別會實作可以加入功能區列、 功能區面板或功能區的快顯功能表的下拉式方塊控制項。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCRibbonComboBox : public CMFCRibbonEdit  
```  
  
## <a name="members"></a>成員  
  
### <a name="constructors"></a>建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCRibbonComboBox::CMFCRibbonComboBox](#cmfcribboncombobox)|建構 CMFCRibbonComboBox 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCRibbonComboBox::AddItem](#additem)|將唯一的項目附加至清單方塊。|  
|[CMFCRibbonComboBox::DeleteItem](#deleteitem)|從清單方塊中刪除指定的項目。|  
|[CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize)|指定清單方塊是否可以卸除向下變更大小。|  
|[CMFCRibbonComboBox::FindItem](#finditem)|傳回符合指定的字串清單方塊中的第一個項目的索引。|  
|[CMFCRibbonComboBox::GetCount](#getcount)|清單方塊中，傳回的項目數。|  
|[CMFCRibbonComboBox::GetCurSel](#getcursel)|清單方塊中，取得目前選取之項目的索引。|  
|[CMFCRibbonComboBox::GetDropDownHeight](#getdropdownheight)|下拉式清單方塊時，取得清單方塊的高度。|  
|[CMFCRibbonComboBox::GetIntermediateSize](#getintermediatesize)|傳回中繼模式中顯示下拉式方塊的大小。|  
|[CMFCRibbonComboBox::GetItem](#getitem)|傳回與清單方塊中的指定索引處的項目相關聯的字串。|  
|[CMFCRibbonComboBox::GetItemData](#getitemdata)|傳回與清單方塊中的指定索引處的項目相關聯的資料。|  
|[CMFCRibbonComboBox::HasEditBox](#haseditbox)|表示控制項是否包含編輯方塊。|  
|[CMFCRibbonComboBox::IsResizeDropDownList](#isresizedropdownlist)|指出可以調整大小的清單方塊。|  
|[CMFCRibbonComboBox::OnSelectItem](#onselectitem)|當使用者選取項目在清單方塊中，由架構呼叫。|  
|[CMFCRibbonComboBox::RemoveAllItems](#removeallitems)|刪除所有項目從清單方塊，並清除 [編輯] 方塊。|  
|[CMFCRibbonComboBox::SelectItem](#selectitem)|清單方塊中選取項目。|  
|[CMFCRibbonComboBox::SetDropDownHeight](#setdropdownheight)|向下拖曳時，請設定清單方塊的高度。|  
  
## <a name="remarks"></a>備註  
 功能區下拉式方塊包含結合的靜態標籤 」 或 「 使用者可以編輯的標籤清單方塊。 您必須指定您想要建立您在功能區下拉式方塊的型別。  
  
## <a name="example"></a>範例  
 下列範例示範如何建構的物件`CMFCRibbonComboBox`類別、 將項目加入至下拉式方塊、 下拉式方塊中，選取項目和面板加入下拉式方塊。  
  
 [!code-cpp[NVC_MFC_RibbonApp#11](../../mfc/reference/codesnippet/cpp/cmfcribboncombobox-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)  
  
 [CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxribboncombobox.h  
  
##  <a name="additem"></a>CMFCRibbonComboBox::AddItem  
 將唯一的項目附加至清單方塊。  
  
```  
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,  
    DWORD_PTR dwData=0);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszItem`  
 要加入之項目的字串。  
  
 [in] `dwData`  
 要加入的項目與相關的資料。  
  
### <a name="return-value"></a>傳回值  
 附加的項目以零為起始的索引。  
  
##  <a name="cmfcribboncombobox"></a>CMFCRibbonComboBox::CMFCRibbonComboBox  
 建構 `CMFCRibbonComboBox` 物件。  
  
```  
public:  
CMFCRibbonComboBox(
    UINT nID,  
    BOOL bHasEditBox=TRUE,  
    Int nWidth=-1,  
    LPCTSTR lpszLabel=NULL,  
    Int nImage=-1);

protected:  
CMFCRibbonComboBox();
```  
  
### <a name="parameters"></a>參數  
 [in] `nID`  
 下拉式方塊的識別碼。  
  
 [in] `bHasEditBox`  
 `TRUE`如果您想編輯方塊控制項; 內`FALSE`否則。  
  
 [in] `nWidth`  
 像素為單位; 下拉式方塊的寬度或-1 可進行的預設寬度。  
  
 [in] `lpszLabel`  
 下拉式方塊顯示標籤。  
  
 [in] `nImage`  
 下拉式方塊的小型影像索引。  
  
### <a name="remarks"></a>備註  
 預設寬度是 108 像素為單位。  
  
##  <a name="deleteitem"></a>CMFCRibbonComboBox::DeleteItem  
 從清單方塊中刪除指定的項目。  
  
```  
BOOL DeleteItem(int iIndex);
BOOL DeleteItem(DWORD_PTR dwData);

BOOL DeleteItem(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>參數  
 [in] `iIndex`  
 要刪除的項目以零為起始的索引。  
  
 [in] `dwData`  
 要刪除的項目與相關的資料。  
  
 [in] `lpszText`  
 要刪除之項目的字串。 如果有多個項目，使用相同的字串，則會刪除第一個項目。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果指定的項目已遭到刪除。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="enabledropdownlistresize"></a>CMFCRibbonComboBox::EnableDropDownListResize  
 指定清單方塊是否可以卸除向下變更大小。  
  
```  
void EnableDropDownListResize(BOOL bEnable=FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bEnable`  
 `TRUE`若要啟用 調整大小;`FALSE`停用調整大小。  
  
### <a name="remarks"></a>備註  
 啟用時調整大小，清單方塊將會變更大小，以符合它所顯示的項目。  
  
##  <a name="finditem"></a>CMFCRibbonComboBox::FindItem  
 傳回符合指定的字串清單方塊中的第一個項目的索引。  
  
```  
int FindItem(LPCTSTR lpszText) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszText`  
 清單方塊中項目的字串。  
  
### <a name="return-value"></a>傳回值  
 以零起始的索引的項目。或是-1，如果找不到項目。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getcount"></a>CMFCRibbonComboBox::GetCount  
 清單方塊中，傳回的項目數。  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 在清單方塊中或 0，表示清單方塊不包含的任何項目中的項目數目。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getcursel"></a>CMFCRibbonComboBox::GetCurSel  
 清單方塊中，取得目前選取之項目的索引。  
  
```  
int GetCurSel() const;  
```  
  
### <a name="return-value"></a>傳回值  
 在清單方塊中，目前選取之項目的以零起始的索引則為-1 會選取任何項目。  
  
##  <a name="getdropdownheight"></a>CMFCRibbonComboBox::GetDropDownHeight  
 下拉式清單方塊時，取得清單方塊的高度。  
  
```  
int GetDropDownHeight();
```  
  
### <a name="return-value"></a>傳回值  
 高度 （像素為單位的清單方塊）。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getintermediatesize"></a>CMFCRibbonComboBox::GetIntermediateSize  
 傳回中繼模式中顯示下拉式方塊的大小。  
  
```  
virtual CSize GetIntermediateSize(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 下拉式方塊的裝置內容的指標。  
  
### <a name="return-value"></a>傳回值  
 下拉式方塊的大小。  
  
### <a name="remarks"></a>備註  
 顯示小型影像時傳回的大小會根據下拉式方塊的大小。  
  
##  <a name="getitem"></a>CMFCRibbonComboBox::GetItem  
 傳回與清單方塊中的指定索引處的項目相關聯的字串。  
  
```  
LPCTSTR GetItem(int iIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `iIndex`  
 清單方塊中的項目以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 項目; 相關聯的字串指標否則，`NULL`如果索引參數無效，或者索引參數是-1，下拉式方塊中選取任何項目。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getitemdata"></a>CMFCRibbonComboBox::GetItemData  
 傳回與清單方塊中的指定索引處的項目相關聯的資料。  
  
```  
DWORD_PTR GetItemData(int iIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `iIndex`  
 清單方塊中的項目以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 與項目; 相關聯的資料0 或如果此項目不存在，或者索引參數是-1，清單方塊中沒有選取項目。  
  
##  <a name="haseditbox"></a>CMFCRibbonComboBox::HasEditBox  
 表示控制項是否包含編輯方塊。  
  
```  
BOOL HasEditBox() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果控制項包含編輯方塊。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="isresizedropdownlist"></a>CMFCRibbonComboBox::IsResizeDropDownList  
 指出可以調整大小的清單方塊。  
  
```  
BOOL IsResizeDropDownList() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果清單方塊可以調整大小;否則`FALSE`。 [CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize)  
  
### <a name="remarks"></a>備註  
 您可以使用調整大小的清單方塊來啟用[CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize)方法。  
  
##  <a name="onselectitem"></a>CMFCRibbonComboBox::OnSelectItem  
 當使用者選取項目在清單方塊中，由架構呼叫。  
  
```  
virtual void OnSelectItem(int nItem);
```  
  
### <a name="parameters"></a>參數  
 [in] `nItem`  
 選取之項目的索引。  
  
### <a name="remarks"></a>備註  
 如果您想要處理使用者輸入選取範圍，請覆寫這個方法。  
  
##  <a name="removeallitems"></a>CMFCRibbonComboBox::RemoveAllItems  
 刪除所有項目從清單方塊，並清除 [編輯] 方塊。  
  
```  
void RemoveAllItems();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="selectitem"></a>CMFCRibbonComboBox::SelectItem  
 清單方塊中選取項目。  
  
```  
BOOL SelectItem(int iIndex);
BOOL SelectItem(DWORD_PTR dwData);

BOOL SelectItem(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>參數  
 [in] `iIndex`  
 清單方塊中的項目以零為起始的索引。  
  
 [in] `dwData`  
 清單方塊中的項目與相關的資料。  
  
 [in] `lpszText`  
 清單方塊中項目的字串。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果該方法成功。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="setdropdownheight"></a>CMFCRibbonComboBox::SetDropDownHeight  
 向下拖曳時，請設定清單方塊的高度。  
  
```  
void SetDropDownHeight(int nHeight);
```  
  
### <a name="parameters"></a>參數  
 [in] `nHeight`  
 高度 （像素為單位的清單方塊）。  
  
### <a name="remarks"></a>備註  
 預設高度為 150 像素。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonEdit 類別](../../mfc/reference/cmfcribbonedit-class.md)
