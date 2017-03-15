---
title: "CMFCKeyMapDialog 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCKeyMapDialog
dev_langs:
- C++
helpviewer_keywords:
- CMFCKeyMapDialog class
ms.assetid: 5feb4942-d636-462d-a162-0104dd320f4e
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
ms.openlocfilehash: 6599f5c3cda6eb407f4545d42528c1c68950b94c
ms.lasthandoff: 02/24/2017

---
# <a name="cmfckeymapdialog-class"></a>CMFCKeyMapDialog 類別
`CMFCKeyMapDialog`類別支援將命令對應至鍵盤按鍵的控制項。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCKeyMapDialog : public CDialogEx  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCKeyMapDialog::CMFCKeyMapDialog](#cmfckeymapdialog)|建構 `CMFCKeyMapDialog` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCKeyMapDialog::DoModal](#domodal)|顯示鍵盤對應 對話方塊。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCKeyMapDialog::FormatItem](#formatitem)|若要建置描述的索引鍵對應的字串架構呼叫。 根據預設，字串會包含命令名稱、 使用的快速鍵和快顯重要描述。|  
|[CMFCKeyMapDialog::GetCommandKeys](#getcommandkeys)|擷取字串，包含與指定的命令相關聯的快速鍵的清單。|  
|[CMFCKeyMapDialog::OnInsertItem](#oninsertitem)|架構支援鍵盤對應控制項的內部清單控制項中插入新項目之前呼叫。|  
|[CMFCKeyMapDialog::OnPrintHeader](#onprintheader)|新的頁面上列印的鍵盤對應的標頭的架構所呼叫。|  
|[CMFCKeyMapDialog::OnPrintItem](#onprintitem)|若要列印的鍵盤對應項目架構呼叫。|  
|[CMFCKeyMapDialog::OnSetColumns](#onsetcolumns)|若要設定支援鍵盤對應控制項的內部清單控制項中的資料行標題架構呼叫。|  
|[CMFCKeyMapDialog::PrintKeyMap](#printkeymap)|當使用者按一下時，由框架呼叫**列印** 按鈕。|  
|[CMFCKeyMapDialog::SetColumnsWidth](#setcolumnswidth)|若要設定支援鍵盤對應控制項的內部清單控制項中的資料行的寬度架構呼叫。|  
  
## <a name="remarks"></a>備註  
 使用`CMFCKeyMapDialog`類別來實作可調整大小的鍵盤對應 對話方塊。 對話方塊中會使用清單檢視控制項來顯示鍵盤快速鍵和其相關聯的命令。  
  
 若要使用`CMFCKeyMapDialog`類別在應用程式中，做為參數傳遞指標到主框架視窗`CMFCKeyMapDialog`建構函式。 然後呼叫`DoModal`方法，以啟動強制回應對話方塊。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDialogEx](../../mfc/reference/cdialogex-class.md)  
  
 [CMFCKeyMapDialog](../../mfc/reference/cmfckeymapdialog-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxkeymapdialog.h  
  
##  <a name="a-namecmfckeymapdialoga--cmfckeymapdialogcmfckeymapdialog"></a><a name="cmfckeymapdialog"></a>CMFCKeyMapDialog::CMFCKeyMapDialog  
 建構 `CMFCKeyMapDialog` 物件。  
  
```  
CMFCKeyMapDialog(
    CFrameWnd* pWndParentFrame,  
    BOOL bEnablePrint=FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `pWndParentFrame`  
 父視窗的指標`CMFCKeyMapDialog`物件。  
  
 [in] `bEnablePrint`  
 `TRUE`如果可以列印快速鍵的清單。，否則， `FALSE`。 預設為 `FALSE`。  
  
### <a name="remarks"></a>備註  
  
### <a name="example"></a>範例  
 下列範例示範如何建構的物件`CMFCKeyMapDialog`類別。 這個範例是屬於[Visual Studio 示範範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo #&21;](../../mfc/codesnippet/cpp/cmfckeymapdialog-class_1.cpp)]  
  
##  <a name="a-namedomodala--cmfckeymapdialogdomodal"></a><a name="domodal"></a>CMFCKeyMapDialog::DoModal  
 顯示鍵盤對應 對話方塊。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>傳回值  
 帶正負號的整數，例如`IDOK`或`IDCANCEL`，也就是傳遞至[CDialog::EndDialog](../../mfc/reference/cdialog-class.md#enddialog)方法。 方法接著會關閉對話方塊。 如需詳細資訊，請參閱[CDialog::DoModal](../../mfc/reference/cdialog-class.md#domodal)。  
  
### <a name="remarks"></a>備註  
 鍵盤對應 對話方塊可讓您選取，並將快速鍵指派給各種類別目錄的命令。 此外，您可以將所選的快速鍵，以及其描述複製到剪貼簿。  
  
##  <a name="a-nameformatitema--cmfckeymapdialogformatitem"></a><a name="formatitem"></a>CMFCKeyMapDialog::FormatItem  
 若要建置描述的索引鍵對應的字串架構呼叫。 根據預設，字串會包含命令名稱、 使用的快速鍵和快顯重要描述。  
  
```  
virtual CString FormatItem(int nItem) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `nItem`  
 索引鍵對應的內部清單中項目的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 A`CString`物件，其中包含已格式化的項目文字。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetcommandkeysa--cmfckeymapdialoggetcommandkeys"></a><a name="getcommandkeys"></a>CMFCKeyMapDialog::GetCommandKeys  
 擷取字串值。 字串包含指定的命令相關聯的快速鍵的清單。  
  
```  
virtual CString GetCommandKeys(UINT uiCmdID) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `uiCmdID`  
 命令 id。  
  
### <a name="return-value"></a>傳回值  
 以分號分隔 （';'） 的快速鍵清單與指定的命令相關聯。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameoninsertitema--cmfckeymapdialogoninsertitem"></a><a name="oninsertitem"></a>CMFCKeyMapDialog::OnInsertItem  
 架構支援鍵盤對應控制項的內部清單控制項插入新項目之前呼叫。  
  
```  
virtual void OnInsertItem(
    CMFCToolBarButton* pButton,  
    int nItem);
```  
  
### <a name="parameters"></a>參數  
 [in] `pButton`  
 指標用來對應的鍵盤快速鍵命令名稱和描述的工具列按鈕。 索引鍵對應項目會儲存在內部清單控制項。  
  
 [in] `nItem`  
 以零為起始的索引，指定要插入新的索引鍵對應項目內部清單控制項中的位置。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonprintheadera--cmfckeymapdialogonprintheader"></a><a name="onprintheader"></a>CMFCKeyMapDialog::OnPrintHeader  
 新的頁面上列印的鍵盤對應的標頭的架構所呼叫。  
  
```  
virtual int OnPrintHeader(
    CDC& dc,  
    int nPage,  
    int cx) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `dc`  
 印表機裝置內容。  
  
 [in] `nPage`  
 若要列印的頁碼。  
  
 [in] `cx`  
 標頭，單位為像素水平位移。  
  
### <a name="return-value"></a>傳回值  
 如果成功，印刷文字的高度。 如需詳細資訊，請參閱 > 一節會傳回值[CDC::DrawText](../../mfc/reference/cdc-class.md#drawtext)。  
  
### <a name="remarks"></a>備註  
 架構會使用這個方法列印鍵盤對應。 根據預設，這個方法會列印的頁面數目、 應用程式名稱和對話方塊的標題。  
  
##  <a name="a-nameonprintitema--cmfckeymapdialogonprintitem"></a><a name="onprintitem"></a>CMFCKeyMapDialog::OnPrintItem  
 若要列印的鍵盤對應項目架構呼叫。  
  
```  
virtual int OnPrintItem(
    CDC& dc,  
    int nItem,  
    int y,  
    int cx,  
    BOOL bCalcHeight) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `dc`  
 印表機裝置內容。  
  
 [in] `nItem`  
 若要列印的項目以零為起始的索引。  
  
 [in] `y`  
 頁面頂端和項目的位置之間的垂直位移。  
  
 [in] `cx`  
 頁面的左邊和位置的項目之間的水平位移。  
  
 [in] `bCalcHeight`  
 `TRUE`計算最佳的高度，列印的項目。`FALSE`截斷列印項目，使其符合預設的空間。  
  
### <a name="return-value"></a>傳回值  
 列印項目的高度。  
  
### <a name="remarks"></a>備註  
 架構會呼叫這個方法，以列印索引鍵對應對話方塊項目。 根據預設，這個方法會列印項目的命令名稱、 快速鍵和命令的描述。  
  
##  <a name="a-nameonsetcolumnsa--cmfckeymapdialogonsetcolumns"></a><a name="onsetcolumns"></a>CMFCKeyMapDialog::OnSetColumns  
 若要設定支援鍵盤對應控制項的內部清單控制項中的資料行標題架構呼叫。  
  
```  
virtual void OnSetColumns();
```  
  
### <a name="remarks"></a>備註  
 根據預設，這個方法會從三個資源取得的資料行的標題。 命令資料行標題是來自 IDS_AFXBARRES_COMMAND、 索引鍵資料行標題是從 IDS_AFXBARRES_KEYS，且描述資料行標題是從 IDS_AFXBARRES_DESCRIPTION。  
  
##  <a name="a-nameprintkeymapa--cmfckeymapdialogprintkeymap"></a><a name="printkeymap"></a>CMFCKeyMapDialog::PrintKeyMap  
 當使用者按一下時，由框架呼叫**列印** 按鈕。  
  
```  
virtual void PrintKeyMap();
```  
  
### <a name="remarks"></a>備註  
 `PrintKeyMap`方法會列印索引鍵的對應。 它會初始化一個新的列印工作，然後重複呼叫[CMFCKeyMapDialog::OnPrintHeader](#onprintheader)和[CMFCKeyMapDialog::OnPrintItem](#onprintitem)方法，直到所有索引鍵的對應時，會列印。  
  
##  <a name="a-namesetcolumnswidtha--cmfckeymapdialogsetcolumnswidth"></a><a name="setcolumnswidth"></a>CMFCKeyMapDialog::SetColumnsWidth  
 若要設定支援鍵盤對應控制項的內部清單控制項中的資料行的寬度架構呼叫。  
  
```  
virtual void SetColumnsWidth();
```  
  
### <a name="remarks"></a>備註  
 這個方法會將設定內部清單控制項的資料行預設寬度。 首先，會計算捷徑索引鍵資料行的寬度。 然後的剩餘寬度的三分之一會配置到命令資料行，而且其餘的三分之二配置給描述資料行。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CKeyboardManager 類別](../../mfc/reference/ckeyboardmanager-class.md)

