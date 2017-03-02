---
title: "CVSListBox 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CVSListBox
dev_langs:
- C++
helpviewer_keywords:
- CVSListBox::PreTranslateMessage method
- CVSListBox class
ms.assetid: c79be7b4-46ed-4af8-a41e-68962782d8ef
caps.latest.revision: 30
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
ms.openlocfilehash: 4527249fc1a22a1db0623ea46954065fcbd071f4
ms.lasthandoff: 02/24/2017

---
# <a name="cvslistbox-class"></a>CVSListBox 類別
`CVSListBox`類別支援可編輯的清單控制項。  
  
## <a name="syntax"></a>語法  
  
```  
class CVSListBox : public CVSListBoxBase  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CVSListBox::CVSListBox](#cvslistbox)|建構 `CVSListBox` 物件。|  
|`CVSListBox::~CVSListBox`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CVSListBox::AddItem](#additem)|將字串加入至清單控制項。 (覆寫 `CVSListBoxBase::AddItem`。)|  
|[CVSListBox::EditItem](#edititem)|啟動清單控制項項目的文字編輯作業。 (覆寫 `CVSListBoxBase::EditItem`。)|  
|[CVSListBox::GetCount](#getcount)|擷取可編輯的清單控制項中的字串數目。 (覆寫 `CVSListBoxBase::GetCount`。)|  
|[CVSListBox::GetItemData](#getitemdata)|擷取可編輯的清單控制項項目相關聯的特定應用程式的 32 位元值。 (覆寫 `CVSListBoxBase::GetItemData`。)|  
|[CVSListBox::GetItemText](#getitemtext)|擷取可編輯的清單控制項項目的文字。 (覆寫 `CVSListBoxBase::GetItemText`。)|  
|[CVSListBox::GetSelItem](#getselitem)|擷取可編輯的清單控制項中目前選取項目的以零為起始的索引。 (覆寫 `CVSListBoxBase::GetSelItem`。)|  
|`CVSListBox::PreTranslateMessage`|轉譯的視窗訊息，再分派給[TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955)和[DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函式。 如需詳細資訊和方法語法，請參閱[CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。 (覆寫 `CVSListBoxBase::PreTranslateMessage`。)|  
|[CVSListBox::RemoveItem](#removeitem)|可編輯的清單控制項中移除的項目。 (覆寫 `CVSListBoxBase::RemoveItem`。)|  
|[CVSListBox::SelectItem](#selectitem)|選取的可編輯的清單控制項的字串。 (覆寫 `CVSListBoxBase::SelectItem`。)|  
|[CVSListBox::SetItemData](#setitemdata)|關聯的可編輯的清單控制項項目之特定應用程式的 32 位元值。 (覆寫 `CVSListBoxBase::SetItemData`。)|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CVSListBox::GetListHwnd](#getlisthwnd)|傳回目前的內嵌的清單檢視控制項的控制代碼。|  
  
## <a name="remarks"></a>備註  
 `CVSListBox`類別提供一組編輯按鈕，可讓使用者建立、 修改、 刪除或重新排列清單控制項中的項目。  
  
 以下是可編輯的清單控制項的圖片。 第二個清單項目，標題為 「&2; 」，這會選取進行編輯。  
  
 ![CVSListBox 控制項](../../mfc/reference/media/cvslistbox.png "cvslistbox")  
  
 如果您將可編輯的清單控制項中使用資源編輯器，請注意，**工具箱**編輯器窗格不會提供預先定義的可編輯的清單控制項。 相反地，例如新增靜態控制項**群組方塊**控制項。 指定大小和可編輯的清單控制項的位置，架構會使用靜態控制項做為預留位置。  
  
 若要使用的可編輯的清單控制項在對話方塊範本中，宣告`CVSListBox`變數中您的對話方塊類別。 若要支援變數與控制項之間的資料交換，定義`DDX_Control`中的巨集項目`DoDataExchange` 對話方塊的方法。 根據預設，建立不含編輯 按鈕可編輯的清單控制項。 您可以使用繼承的 CVSListBoxBase::SetStandardButtons 方法來啟用 [編輯] 按鈕。  
  
 如需詳細資訊，請參閱範例目錄中，`New Controls`範例中，將 Page3.cpp 和 Page3.h 檔案。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CStatic](../../mfc/reference/cstatic-class.md)  
  
 `CVSListBoxBase`  
  
 [CVSListBox](../../mfc/reference/cvslistbox-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxvslistbox.h  
  
##  <a name="a-nameadditema--cvslistboxadditem"></a><a name="additem"></a>CVSListBox::AddItem  
 將字串加入至清單控制項。  
  
```  
virtual int AddItem(
    const CString& strIext,  
    DWORD_PTR dwData=0,  
    int iIndex=-1);
```  
  
### <a name="parameters"></a>參數  
 [in] `strIext`  
 字串的參考。  
  
 [in] `dwData`  
 特定應用程式的 32 位元值與字串相關聯。 預設值為 0。  
  
 [in] `iIndex`  
 將保留字串的位置以零為起始的索引。 如果`iIndex`參數為-1，字串會新增至清單的結尾。 預設值為 -1。  
  
### <a name="return-value"></a>傳回值  
 字串的清單控制項中的位置以零為起始的索引。  
  
### <a name="remarks"></a>備註  
 使用[CVSListBox::GetItemData](#getitemdata)方法來擷取所指定的值`dwData`參數。 這個值可以是應用程式特定整數或其他資料的指標。  
  
##  <a name="a-namecvslistboxa--cvslistboxcvslistbox"></a><a name="cvslistbox"></a>CVSListBox::CVSListBox  
 建構 `CVSListBox` 物件。  
  
```  
CVSListBox();
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameedititema--cvslistboxedititem"></a><a name="edititem"></a>CVSListBox::EditItem  
 啟動清單控制項項目的文字編輯作業。  
  
```  
virtual BOOL EditItem(int iIndex);
```  
  
### <a name="parameters"></a>參數  
 [in] `iIndex`  
 清單控制項項目的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果編輯作業成功; 啟動否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 在使用者開始編輯作業，連按兩下某個項目的標籤，或按下**F2**或**空格鍵**索引鍵的項目有焦點時。  
  
##  <a name="a-namegetcounta--cvslistboxgetcount"></a><a name="getcount"></a>CVSListBox::GetCount  
 擷取可編輯的清單控制項中的字串數目。  
  
```  
virtual int GetCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 清單控制項中的項目數。  
  
### <a name="remarks"></a>備註  
 請注意此計數是比最後一個項目的索引值大一因為是以零為起始的索引。  
  
##  <a name="a-namegetitemdataa--cvslistboxgetitemdata"></a><a name="getitemdata"></a>CVSListBox::GetItemData  
 擷取可編輯的清單控制項項目相關聯的特定應用程式的 32 位元值。  
  
```  
virtual DWORD_PTR GetItemData(int iIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `iIndex`  
 可編輯的清單控制項項目的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 指定的項目相關聯的 32 位元值。  
  
### <a name="remarks"></a>備註  
 使用[CVSListBox::SetItemData](#setitemdata)或[CVSListBox::AddItem](#additem)要與清單控制項項目產生關聯的 32 位元值的方法。 這個值可以是應用程式特定整數或其他資料的指標。  
  
##  <a name="a-namegetitemtexta--cvslistboxgetitemtext"></a><a name="getitemtext"></a>CVSListBox::GetItemText  
 擷取可編輯的清單控制項項目的文字。  
  
```  
virtual CString GetItemText(int iIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `iIndex`  
 可編輯的清單控制項項目的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md)物件，其中包含指定項目的文字。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetlisthwnda--cvslistboxgetlisthwnd"></a><a name="getlisthwnd"></a>CVSListBox::GetListHwnd  
 傳回目前的內嵌的清單檢視控制項的控制代碼。  
  
```  
virtual HWND GetListHwnd() const;  
```  
  
### <a name="return-value"></a>傳回值  
 內嵌的清單檢視控制項的控制代碼。  
  
### <a name="remarks"></a>備註  
 使用此方法來擷取支援內嵌的清單檢視控制項的控制代碼`CVSListBox`類別。  
  
##  <a name="a-namegetselitema--cvslistboxgetselitem"></a><a name="getselitem"></a>CVSListBox::GetSelItem  
 擷取可編輯的清單控制項中目前選取項目的以零為起始的索引。  
  
```  
virtual int GetSelItem() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，起始的索引，目前選取的項目。反之則為-1。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameremoveitema--cvslistboxremoveitem"></a><a name="removeitem"></a>CVSListBox::RemoveItem  
 可編輯的清單控制項中移除的項目。  
  
```  
virtual BOOL RemoveItem(int iIndex);
```  
  
### <a name="parameters"></a>參數  
 [in] `iIndex`  
 可編輯的清單控制項項目的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果指定的項目已移除;否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameselectitema--cvslistboxselectitem"></a><a name="selectitem"></a>CVSListBox::SelectItem  
 選取的可編輯的清單控制項的字串。  
  
```  
virtual BOOL SelectItem(int iItem);
```  
  
### <a name="parameters"></a>參數  
 [in] `iItem`  
 可編輯的清單控制項項目的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `TRUE`；否則為 `FALSE`。  
  
### <a name="remarks"></a>備註  
 這個方法會選取指定的項目，而且如有必要，將項目捲動到檢視。  
  
##  <a name="a-namesetitemdataa--cvslistboxsetitemdata"></a><a name="setitemdata"></a>CVSListBox::SetItemData  
 關聯的可編輯的清單控制項項目之特定應用程式的 32 位元值。  
  
```  
virtual void SetItemData(
    int iIndex,  
    DWORD_PTR dwData);
```  
  
### <a name="parameters"></a>參數  
 [in] `iIndex`  
 可編輯的清單控制項項目的以零為起始的索引。  
  
 [in] `dwData`  
 32 位元值。 這個值可以是應用程式特定整數或其他資料的指標。  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)

