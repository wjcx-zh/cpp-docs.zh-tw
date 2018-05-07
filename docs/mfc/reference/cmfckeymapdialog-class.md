---
title: CMFCKeyMapDialog 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCKeyMapDialog
- AFXKEYMAPDIALOG/CMFCKeyMapDialog
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::CMFCKeyMapDialog
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::DoModal
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::FormatItem
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::GetCommandKeys
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnInsertItem
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnPrintHeader
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnPrintItem
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnSetColumns
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::PrintKeyMap
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::SetColumnsWidth
dev_langs:
- C++
helpviewer_keywords:
- CMFCKeyMapDialog [MFC], CMFCKeyMapDialog
- CMFCKeyMapDialog [MFC], DoModal
- CMFCKeyMapDialog [MFC], FormatItem
- CMFCKeyMapDialog [MFC], GetCommandKeys
- CMFCKeyMapDialog [MFC], OnInsertItem
- CMFCKeyMapDialog [MFC], OnPrintHeader
- CMFCKeyMapDialog [MFC], OnPrintItem
- CMFCKeyMapDialog [MFC], OnSetColumns
- CMFCKeyMapDialog [MFC], PrintKeyMap
- CMFCKeyMapDialog [MFC], SetColumnsWidth
ms.assetid: 5feb4942-d636-462d-a162-0104dd320f4e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 25d86a4797479fe3ee95dde162e22cde63aaa71e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cmfckeymapdialog-class"></a>CMFCKeyMapDialog 類別
`CMFCKeyMapDialog`類別支援將命令對應至鍵盤上的按鍵的控制項。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCKeyMapDialog : public CDialogEx  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCKeyMapDialog::CMFCKeyMapDialog](#cmfckeymapdialog)|建構 `CMFCKeyMapDialog` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCKeyMapDialog::DoModal](#domodal)|顯示鍵盤對應 對話方塊。|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCKeyMapDialog::FormatItem](#formatitem)|由架構呼叫以建立描述索引鍵對應的字串。 根據預設，字串會包含命令名稱、 使用的快速鍵和快顯金鑰描述。|  
|[CMFCKeyMapDialog::GetCommandKeys](#getcommandkeys)|擷取字串，包含與指定的命令相關聯的快速鍵的清單。|  
|[CMFCKeyMapDialog::OnInsertItem](#oninsertitem)|新的項目插入內部清單控制項支援的鍵盤對應控制項之前由架構呼叫。|  
|[CMFCKeyMapDialog::OnPrintHeader](#onprintheader)|由架構呼叫以列印新的頁面上的鍵盤對應的標頭。|  
|[CMFCKeyMapDialog::OnPrintItem](#onprintitem)|由架構呼叫以列印鍵盤對應項目。|  
|[CMFCKeyMapDialog::OnSetColumns](#onsetcolumns)|由架構呼叫以設定支援鍵盤對應控制項的內部清單控制項中的資料行的標題。|  
|[CMFCKeyMapDialog::PrintKeyMap](#printkeymap)|由架構呼叫，當使用者按一下**列印** 按鈕。|  
|[CMFCKeyMapDialog::SetColumnsWidth](#setcolumnswidth)|由架構呼叫以支援鍵盤對應控制項的內部清單控制項中設定資料行的寬度。|  
  
## <a name="remarks"></a>備註  
 使用`CMFCKeyMapDialog`類別來實作可調整大小的鍵盤對應 對話方塊。 對話方塊會使用清單檢視控制項來顯示鍵盤快速鍵和其相關聯的命令。  
  
 若要使用`CMFCKeyMapDialog`類別在應用程式中，當做參數傳遞指標主框架視窗`CMFCKeyMapDialog`建構函式。 然後呼叫`DoModal`方法啟動強制回應對話方塊。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDialogEx](../../mfc/reference/cdialogex-class.md)  
  
 [CMFCKeyMapDialog](../../mfc/reference/cmfckeymapdialog-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxkeymapdialog.h  
  
##  <a name="cmfckeymapdialog"></a>  CMFCKeyMapDialog::CMFCKeyMapDialog  
 建構 `CMFCKeyMapDialog` 物件。  
  
```  
CMFCKeyMapDialog(
    CFrameWnd* pWndParentFrame,  
    BOOL bEnablePrint=FALSE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pWndParentFrame`  
 父視窗的指標`CMFCKeyMapDialog`物件。  
  
 [輸入] `bEnablePrint`  
 `TRUE` 如果可以列印快速鍵的清單。，否則， `FALSE`。 預設值為 `FALSE`。  
  
### <a name="remarks"></a>備註  
  
### <a name="example"></a>範例  
 下列範例示範如何建構的物件`CMFCKeyMapDialog`類別。 這個範例是屬於[Visual Studio 示範範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#21](../../mfc/codesnippet/cpp/cmfckeymapdialog-class_1.cpp)]  
  
##  <a name="domodal"></a>  CMFCKeyMapDialog::DoModal  
 顯示鍵盤對應 對話方塊。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>傳回值  
 帶正負號的整數，例如`IDOK`或`IDCANCEL`，也就是傳遞至[CDialog::EndDialog](../../mfc/reference/cdialog-class.md#enddialog)方法。 方法，接著，關閉對話方塊。 如需詳細資訊，請參閱[CDialog::DoModal](../../mfc/reference/cdialog-class.md#domodal)。  
  
### <a name="remarks"></a>備註  
 鍵盤對應 對話方塊可讓您選取，並將快速鍵指派給各種類別目錄的命令。 此外，您可以將選取的快速鍵，以及其描述複製到剪貼簿。  
  
##  <a name="formatitem"></a>  CMFCKeyMapDialog::FormatItem  
 由架構呼叫以建立描述索引鍵對應的字串。 根據預設，字串會包含命令名稱、 使用的快速鍵和快顯金鑰描述。  
  
```  
virtual CString FormatItem(int nItem) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸入] `nItem`  
 索引鍵對應的內部清單中項目的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 A`CString`物件，其中包含已格式化的項目文字。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getcommandkeys"></a>  CMFCKeyMapDialog::GetCommandKeys  
 擷取字串值。 字串包含指定的命令相關聯的快速鍵的清單。  
  
```  
virtual CString GetCommandKeys(UINT uiCmdID) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸入] `uiCmdID`  
 命令 id。  
  
### <a name="return-value"></a>傳回值  
 以分號分隔 （';'） 的快速鍵清單與指定的命令相關聯。  
  
### <a name="remarks"></a>備註  
  
##  <a name="oninsertitem"></a>  CMFCKeyMapDialog::OnInsertItem  
 支援的鍵盤對應控制項的內部清單控制項插入新項目之前，由架構呼叫。  
  
```  
virtual void OnInsertItem(
    CMFCToolBarButton* pButton,  
    int nItem);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pButton`  
 指標用來對應鍵盤按鍵的組合來建立命令名稱與描述工具列按鈕。 索引鍵對應項目會儲存在內部清單控制項中。  
  
 [輸入] `nItem`  
 以零為起始的索引，指定要插入新的索引鍵對應項目內部清單控制項中的位置。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onprintheader"></a>  CMFCKeyMapDialog::OnPrintHeader  
 由架構呼叫以列印新的頁面上的鍵盤對應的標頭。  
  
```  
virtual int OnPrintHeader(
    CDC& dc,  
    int nPage,  
    int cx) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸入] `dc`  
 印表機裝置內容。  
  
 [輸入] `nPage`  
 若要列印的頁碼。  
  
 [輸入] `cx`  
 標頭，單位為像素水平位移。  
  
### <a name="return-value"></a>傳回值  
 如果成功的話，列印文字的高度。 如需詳細資訊，請參閱 > 一節會傳回值[CDC::DrawText](../../mfc/reference/cdc-class.md#drawtext)。  
  
### <a name="remarks"></a>備註  
 架構會使用這個方法列印鍵盤對應。 根據預設，這個方法會列印的頁碼，應用程式名稱和對話方塊的標題。  
  
##  <a name="onprintitem"></a>  CMFCKeyMapDialog::OnPrintItem  
 由架構呼叫以列印鍵盤對應項目。  
  
```  
virtual int OnPrintItem(
    CDC& dc,  
    int nItem,  
    int y,  
    int cx,  
    BOOL bCalcHeight) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸入] `dc`  
 印表機裝置內容。  
  
 [輸入] `nItem`  
 若要列印的項目以零為起始的索引。  
  
 [輸入] `y`  
 頁面頂端和項目的位置之間的垂直位移。  
  
 [輸入] `cx`  
 頁面的左邊和項目的位置之間的水平位移。  
  
 [輸入] `bCalcHeight`  
 `TRUE` 計算最佳的高度，列印的項目。`FALSE`截斷列印項目，使其符合預設的空間。  
  
### <a name="return-value"></a>傳回值  
 列印項目的高度。  
  
### <a name="remarks"></a>備註  
 架構會呼叫這個方法，以列印索引鍵對應對話方塊項目。 根據預設，這個方法會列印項目的命令名稱、 快捷鍵和命令的描述。  
  
##  <a name="onsetcolumns"></a>  CMFCKeyMapDialog::OnSetColumns  
 由架構呼叫以設定支援鍵盤對應控制項的內部清單控制項中的資料行的標題。  
  
```  
virtual void OnSetColumns();
```  
  
### <a name="remarks"></a>備註  
 根據預設，這個方法會從三個資源中取得的資料行的標題。 命令資料行標題來自 IDS_AFXBARRES_COMMAND、 索引鍵資料行標題是從 IDS_AFXBARRES_KEYS，而從 IDS_AFXBARRES_DESCRIPTION 會描述資料行標題。  
  
##  <a name="printkeymap"></a>  CMFCKeyMapDialog::PrintKeyMap  
 由架構呼叫，當使用者按一下**列印** 按鈕。  
  
```  
virtual void PrintKeyMap();
```  
  
### <a name="remarks"></a>備註  
 `PrintKeyMap`方法列印索引鍵對應。 它會初始化一個新的列印工作，然後重複呼叫[CMFCKeyMapDialog::OnPrintHeader](#onprintheader)和[CMFCKeyMapDialog::OnPrintItem](#onprintitem)方法，直到所有索引鍵的對應時，會列印。  
  
##  <a name="setcolumnswidth"></a>  CMFCKeyMapDialog::SetColumnsWidth  
 由架構呼叫以支援鍵盤對應控制項的內部清單控制項中設定資料行的寬度。  
  
```  
virtual void SetColumnsWidth();
```  
  
### <a name="remarks"></a>備註  
 這個方法會將設定內部清單控制項的資料行預設寬度。 首先，會計算捷徑索引鍵資料行的寬度。 然後三分之一的剩餘寬度配置給命令的資料行，而其餘的三分之二配置給 description 資料行。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CKeyboardManager 類別](../../mfc/reference/ckeyboardmanager-class.md)
