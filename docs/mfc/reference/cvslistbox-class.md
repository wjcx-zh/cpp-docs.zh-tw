---
title: CVSListBox 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CVSListBox
- AFXVSLISTBOX/CVSListBox
- AFXVSLISTBOX/CVSListBox::CVSListBox
- AFXVSLISTBOX/CVSListBox::AddItem
- AFXVSLISTBOX/CVSListBox::EditItem
- AFXVSLISTBOX/CVSListBox::GetCount
- AFXVSLISTBOX/CVSListBox::GetItemData
- AFXVSLISTBOX/CVSListBox::GetItemText
- AFXVSLISTBOX/CVSListBox::GetSelItem
- AFXVSLISTBOX/CVSListBox::RemoveItem
- AFXVSLISTBOX/CVSListBox::SelectItem
- AFXVSLISTBOX/CVSListBox::SetItemData
- AFXVSLISTBOX/CVSListBox::GetListHwnd
dev_langs:
- C++
helpviewer_keywords:
- CVSListBox [MFC], CVSListBox
- CVSListBox [MFC], AddItem
- CVSListBox [MFC], EditItem
- CVSListBox [MFC], GetCount
- CVSListBox [MFC], GetItemData
- CVSListBox [MFC], GetItemText
- CVSListBox [MFC], GetSelItem
- CVSListBox [MFC], RemoveItem
- CVSListBox [MFC], SelectItem
- CVSListBox [MFC], SetItemData
- CVSListBox [MFC], GetListHwnd
ms.assetid: c79be7b4-46ed-4af8-a41e-68962782d8ef
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 380b470531fd28d8cfe68aa931105430111c3dbf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cvslistbox-class"></a>CVSListBox 類別
`CVSListBox`類別支援可編輯的清單控制項。  
  
## <a name="syntax"></a>語法  
  
```  
class CVSListBox : public CVSListBoxBase  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CVSListBox::CVSListBox](#cvslistbox)|建構 `CVSListBox` 物件。|  
|`CVSListBox::~CVSListBox`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CVSListBox::AddItem](#additem)|將字串新增至清單控制項。 (覆寫 `CVSListBoxBase::AddItem`。)|  
|[CVSListBox::EditItem](#edititem)|啟動的文字編輯作業的清單控制項項目。 (覆寫 `CVSListBoxBase::EditItem`。)|  
|[CVSListBox::GetCount](#getcount)|擷取可編輯的清單控制項中的字串數目。 (覆寫 `CVSListBoxBase::GetCount`。)|  
|[CVSListBox::GetItemData](#getitemdata)|擷取可編輯的清單控制項項目相關聯的特定應用程式的 32 位元值。 (覆寫 `CVSListBoxBase::GetItemData`。)|  
|[CVSListBox::GetItemText](#getitemtext)|擷取可編輯的清單控制項項目的文字。 (覆寫 `CVSListBoxBase::GetItemText`。)|  
|[CVSListBox::GetSelItem](#getselitem)|擷取可編輯的清單控制項中目前選取之項目的以零為起始的索引。 (覆寫 `CVSListBoxBase::GetSelItem`。)|  
|`CVSListBox::PreTranslateMessage`|將視窗訊息轉譯分派至之前[TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955)和[DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函式。 如需詳細資訊和方法語法，請參閱[cwnd:: Pretranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。 (覆寫 `CVSListBoxBase::PreTranslateMessage`。)|  
|[CVSListBox::RemoveItem](#removeitem)|可編輯的清單控制項中移除的項目。 (覆寫 `CVSListBoxBase::RemoveItem`。)|  
|[CVSListBox::SelectItem](#selectitem)|選取的可編輯的清單控制項字串。 (覆寫 `CVSListBoxBase::SelectItem`。)|  
|[CVSListBox::SetItemData](#setitemdata)|將特定應用程式的 32 位元值與可編輯的清單控制項項目產生關聯。 (覆寫 `CVSListBoxBase::SetItemData`。)|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CVSListBox::GetListHwnd](#getlisthwnd)|傳回目前的內嵌的清單檢視控制項的控制代碼。|  
  
## <a name="remarks"></a>備註  
 `CVSListBox`類別會提供一組編輯按鈕可讓使用者建立、 修改、 刪除或重新排列清單控制項中的項目。  
  
 以下是可編輯的清單控制項的圖片。 第二個清單項目，其標題為"Item2"，會選取進行編輯。  
  
 ![CVSListBox 控制項](../../mfc/reference/media/cvslistbox.png "cvslistbox")  
  
 如果您使用資源編輯器可編輯的清單控制項加入時，請注意，**工具箱**編輯器窗格不提供預先定義的可編輯清單控制項。 相反地，加入靜態控制項類似**群組方塊**控制項。 架構會做為預留位置使用靜態控制項，以指定的大小和位置的可編輯的清單控制項。  
  
 若要使用的可編輯的清單控制項在對話方塊範本中，宣告`CVSListBox`對話方塊類別中的變數。 若要支援變數與控制項之間的資料交換，定義`DDX_Control`巨集項目中的`DoDataExchange` 對話方塊中的方法。 根據預設，建立不含編輯按鈕可編輯的清單控制項。 您可以使用繼承的 CVSListBoxBase::SetStandardButtons 方法來啟用 [編輯] 按鈕。  
  
 如需詳細資訊，請參閱範例目錄中，`New Controls`取樣，請將 Page3.cpp 和 Page3.h 檔案。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CStatic](../../mfc/reference/cstatic-class.md)  
  
 `CVSListBoxBase`  
  
 [CVSListBox](../../mfc/reference/cvslistbox-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxvslistbox.h  
  
##  <a name="additem"></a>  CVSListBox::AddItem  
 將字串新增至清單控制項。  
  
```  
virtual int AddItem(
    const CString& strIext,  
    DWORD_PTR dwData=0,  
    int iIndex=-1);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `strIext`  
 字串的參考。  
  
 [輸入] `dwData`  
 特定應用程式的 32 位元值與字串相關聯。 預設值為 0。  
  
 [輸入] `iIndex`  
 將保留在字串的位置以零為起始的索引。 如果`iIndex`參數為-1，字串會新增至清單的結尾。 預設值為 -1。  
  
### <a name="return-value"></a>傳回值  
 字串清單控制項中的位置以零為起始的索引。  
  
### <a name="remarks"></a>備註  
 使用[CVSListBox::GetItemData](#getitemdata)方法來擷取所指定的值`dwData`參數。 這個值可以是應用程式特定整數或其他資料的指標。  
  
##  <a name="cvslistbox"></a>  CVSListBox::CVSListBox  
 建構 `CVSListBox` 物件。  
  
```  
CVSListBox();
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="edititem"></a>  CVSListBox::EditItem  
 啟動的文字編輯作業的清單控制項項目。  
  
```  
virtual BOOL EditItem(int iIndex);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `iIndex`  
 清單控制項項目的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果編輯作業會成功; 啟動否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 在使用者開始編輯作業，連按兩下某個項目的標籤，或按**F2**或**空格鍵**索引鍵的項目有焦點時。  
  
##  <a name="getcount"></a>  CVSListBox::GetCount  
 擷取可編輯的清單控制項中的字串數目。  
  
```  
virtual int GetCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 清單控制項中的項目數。  
  
### <a name="remarks"></a>備註  
 請注意，計數大於最後一個項目的索引值，因為索引以零為起始。  
  
##  <a name="getitemdata"></a>  CVSListBox::GetItemData  
 擷取可編輯的清單控制項項目相關聯的特定應用程式的 32 位元值。  
  
```  
virtual DWORD_PTR GetItemData(int iIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸入] `iIndex`  
 可編輯的清單控制項項目以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 32 位元值與指定的項目相關聯。  
  
### <a name="remarks"></a>備註  
 使用[CVSListBox::SetItemData](#setitemdata)或[CVSListBox::AddItem](#additem)方法，將 32 位元值與清單控制項項目產生關聯。 這個值可以是應用程式特定整數或其他資料的指標。  
  
##  <a name="getitemtext"></a>  CVSListBox::GetItemText  
 擷取可編輯的清單控制項項目的文字。  
  
```  
virtual CString GetItemText(int iIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸入] `iIndex`  
 可編輯的清單控制項項目以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md)物件，其中包含指定項目的文字。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getlisthwnd"></a>  CVSListBox::GetListHwnd  
 傳回目前的內嵌的清單檢視控制項的控制代碼。  
  
```  
virtual HWND GetListHwnd() const;  
```  
  
### <a name="return-value"></a>傳回值  
 內嵌的清單檢視控制項之控制代碼。  
  
### <a name="remarks"></a>備註  
 使用此方法來擷取支援內嵌的清單檢視控制項的控制代碼`CVSListBox`類別。  
  
##  <a name="getselitem"></a>  CVSListBox::GetSelItem  
 擷取可編輯的清單控制項中目前選取之項目的以零為起始的索引。  
  
```  
virtual int GetSelItem() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，目前選取的項目; 的以零為起始的索引否則為-1。  
  
### <a name="remarks"></a>備註  
  
##  <a name="removeitem"></a>  CVSListBox::RemoveItem  
 可編輯的清單控制項中移除的項目。  
  
```  
virtual BOOL RemoveItem(int iIndex);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `iIndex`  
 可編輯的清單控制項項目以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果已移除指定的項目。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="selectitem"></a>  CVSListBox::SelectItem  
 選取的可編輯的清單控制項字串。  
  
```  
virtual BOOL SelectItem(int iItem);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `iItem`  
 可編輯的清單控制項項目以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `TRUE`；否則為 `FALSE`。  
  
### <a name="remarks"></a>備註  
 此方法會選取指定的項目，而且如有必要，將項目捲動到檢視。  
  
##  <a name="setitemdata"></a>  CVSListBox::SetItemData  
 將特定應用程式的 32 位元值與可編輯的清單控制項項目產生關聯。  
  
```  
virtual void SetItemData(
    int iIndex,  
    DWORD_PTR dwData);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `iIndex`  
 可編輯的清單控制項項目以零為起始的索引。  
  
 [輸入] `dwData`  
 32 位元值。 這個值可以是應用程式特定整數或其他資料的指標。  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)
