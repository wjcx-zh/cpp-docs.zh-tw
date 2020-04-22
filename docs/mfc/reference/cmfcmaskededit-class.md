---
title: CMFCMaskedEdit 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCMaskedEdit
- AFXMASKEDEDIT/CMFCMaskedEdit
- AFXMASKEDEDIT/CMFCMaskedEdit::DisableMask
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableGetMaskedCharsOnly
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableMask
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableSelectByGroup
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableSetMaskedCharsOnly
- AFXMASKEDEDIT/CMFCMaskedEdit::GetWindowText
- AFXMASKEDEDIT/CMFCMaskedEdit::SetValidChars
- AFXMASKEDEDIT/CMFCMaskedEdit::SetWindowText
- AFXMASKEDEDIT/CMFCMaskedEdit::IsMaskedChar
helpviewer_keywords:
- CMFCMaskedEdit [MFC], DisableMask
- CMFCMaskedEdit [MFC], EnableGetMaskedCharsOnly
- CMFCMaskedEdit [MFC], EnableMask
- CMFCMaskedEdit [MFC], EnableSelectByGroup
- CMFCMaskedEdit [MFC], EnableSetMaskedCharsOnly
- CMFCMaskedEdit [MFC], GetWindowText
- CMFCMaskedEdit [MFC], SetValidChars
- CMFCMaskedEdit [MFC], SetWindowText
- CMFCMaskedEdit [MFC], IsMaskedChar
ms.assetid: 13b1a645-2d5d-4c37-8599-16d5003f23a5
ms.openlocfilehash: 26617f10605fe2a8a94adcc477cccab7e2ba4919
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754218"
---
# <a name="cmfcmaskededit-class"></a>CMFCMaskedEdit 類別

該`CMFCMaskedEdit`類支援遮罩編輯控制項,該控件根據掩碼驗證使用者輸入,並根據範本顯示已驗證的結果。

## <a name="syntax"></a>語法

```
class CMFCMaskedEdit : public CEdit
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|`CMFCMaskedEdit::CMFCMaskedEdit`|預設建構函式。|
|`CMFCMaskedEdit::~CMFCMaskedEdit`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFC濛面編輯::D可遮罩](#disablemask)|禁用驗證使用者輸入。|
|[CMFC掃描編輯:僅啟用"只啟用"掃描字元"](#enablegetmaskedcharsonly)|指定`GetWindowText`方法是否僅檢索蒙版字元。|
|[CMFC濛面編輯::啟用蒙版](#enablemask)|初始化遮罩編輯控制件。|
|[CMFCSsedit::啟用選擇群組](#enableselectbygroup)|指定遮罩編輯控制項是選擇特定使用者輸入組還是所有使用者輸入。|
|[CMFC蒙面編輯:僅啟用SetSet](#enablesetmaskedcharsonly)|指定文本是僅針對蒙版字元驗證的,還是針對整個掩碼驗證的。|
|`CMFCMaskedEdit::GetThisClass`|框架用於獲取指向與此類類型關聯的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)物件的指標。|
|[CMFCSsedit 編輯:抓取視窗文字](#getwindowtext)|從蒙版編輯控件檢索已驗證的文本。|
|[CMFC 掃描編輯::設定有效字元](#setvalidchars)|指定使用者可以輸入的有效字元字串。|
|[CMFCSsedit:設定視窗文字](#setwindowtext)|在蒙版編輯控制項中顯示提示。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CMFC蒙面編輯::被蒙塞查爾](#ismaskedchar)|由框架呼叫,以根據相應的遮罩指定的字元。|

## <a name="remarks"></a>備註

執行以下步驟以在`CMFCMaskedEdit`應用程式中使用控制項:

1. 將`CMFCMaskedEdit`物件嵌入到視窗類中。

2. 調用[CMFCMaskedEdit::啟用蒙版](#enablemask)方法以指定掩碼。

3. 呼叫[CMFCMaskedEdit::設定 ValidChars](#setvalidchars)方法以指定有效字元的清單。

4. 呼叫[CMFCMaskedEdit::SetWindowText](#setwindowtext)方法以指定遮罩編輯控制的預設文本。

5. 呼叫[CMFC"解密::獲取視窗文字](#getwindowtext)"方法以檢索已驗證的文本。

如果不調用一個或多個方法初始化蒙版、有效字元和預設文本,則蒙版編輯控制件的操作與標準編輯控件一樣。

## <a name="example"></a>範例

下面的範例展示如何透過使用`EnableMask`方法為蒙版編輯控制項建立掩碼來設置掩碼(例如電話號碼),說明使用者可以輸入的有效字串字串`SetValidChars`的方法,以及`SetWindowText`在蒙版編輯控制項中顯示提示的方法。 此示例是[「新控制件」範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_NewControls#11](../../mfc/reference/codesnippet/cpp/cmfcmaskededit-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#12](../../mfc/reference/codesnippet/cpp/cmfcmaskededit-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

[CMFCMaskedEdit](../../mfc/reference/cmfcmaskededit-class.md)

## <a name="requirements"></a>需求

**標題:** afx 蒙面編輯.h

## <a name="cmfcmaskededitdisablemask"></a><a name="disablemask"></a>CMFC濛面編輯::D可遮罩

禁用驗證使用者輸入。

```cpp
void DisableMask();
```

### <a name="remarks"></a>備註

如果禁用使用者輸入驗證,則蒙版編輯控件的表示方式類似於標準編輯控制項。

## <a name="cmfcmaskededitenablegetmaskedcharsonly"></a><a name="enablegetmaskedcharsonly"></a>CMFC掃描編輯:僅啟用"只啟用"掃描字元"

指定`GetWindowText`方法是否僅檢索蒙版字元。

```cpp
void EnableGetMaskedCharsOnly(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>參數

*b 啟用*<br/>
[在]TRUE 指定[CMFC 蒙面編輯::獲取視窗文本](#getwindowtext)方法僅檢索蒙版字元;FALSE 以指定 該方法檢索整個文本。 預設值為 TRUE。

### <a name="remarks"></a>備註

使用此方法可啟用檢索蒙版字元。 然後創建與電話號碼對應的遮罩編輯控件,例如 (425) 555-0187。 如果調用`GetWindowText`方法 ,它將返回"4255550187"。 如果停用檢索蒙版字元,`GetWindowText`該方法將返回編輯控制項中顯示的文本,例如「(425) 555-0187」。。

## <a name="cmfcmaskededitenablemask"></a><a name="enablemask"></a>CMFC濛面編輯::啟用蒙版

初始化遮罩編輯控制件。

```cpp
void EnableMask(
    LPCTSTR lpszMask,
    LPCTSTR lpszInputTemplate,
    TCHAR chMaskInputTemplate=_T('_'),
    LPCTSTR lpszValid=NULL);
```

### <a name="parameters"></a>參數

*lpsz Mask*<br/>
[在]指定可在使用者輸入中的每個位置顯示的字元類型的遮罩字串。 *lpszInputTemplate*和*lpszMask*參數位串的長度必須相同。 有關蒙版字元的更多詳細資訊,請參閱備註部分。

*lpszInput範本*<br/>
[在]一個遮罩的樣本字串,用於指定可在使用者輸入中的每個位置顯示的文字字元。 使用下劃線字元 ('') 作為字元占位元。 *lpszInputTemplate*和*lpszMask*參數位串的長度必須相同。

*chMask輸入範本*<br/>
[在]框架替換為使用者輸入中每個無效字元的預設字元。 此參數的預設值為下劃線 ("*"。

*lpsz 有效*<br/>
[在]包含一組有效字元的字串。 NULL 表示所有字元都有效。 此參數的預設值為 NULL。

### <a name="remarks"></a>備註

使用此方法為蒙版編輯控制件創建掩碼。 從`CMFCMaskedEdit`類派生類並重寫[CMFCEdit::IsMaskedChar](#ismaskedchar)方法,以使用您自己的代碼進行自定義掩碼處理。

下表列出預設遮罩字元:

|遮罩字元|定義|
|--------------------|----------------|
|D|數位。|
|d|數位或空格。|
|+|加上('+'),減('-')或空格。|
|C|字母字元。|
|c|字母字元或空格。|
|A|字母數字字元。|
|a|字母數字字元或空格。|
|*|可列印字元。|

## <a name="cmfcmaskededitenableselectbygroup"></a><a name="enableselectbygroup"></a>CMFCSsedit::啟用選擇群組

指定遮罩編輯控制件是否允許使用者選擇特定的組輸入或所有輸入。

```cpp
void EnableSelectByGroup(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>參數

*b 啟用*<br/>
[在]TRUE 僅選擇組;FALSE 以選擇整個文字。 預設值為 TRUE。

### <a name="remarks"></a>備註

使用此函數可以指定蒙版編輯控件是允許使用者按組還是整個文本進行選擇。

默認情況下,啟用按組選擇。 在這種情況下,使用者只能選擇連續的有效字元組。

例如,可以使用以下蒙版編輯控制項來驗證電話號碼:

```cpp
m_wndMaskEdit.EnableMask(
    _T(" ddd  ddd dddd"),  // Mask string
    _T("(___) ___-____"),  // Template string
    _T(' '));              // Default char

m_wndMaskEdit.SetValidChars(NULL); // All characters are valid.

m_wndMaskEdit.SetWindowText(_T("(425) 555-0187")); // Prompt
```

如果啟用了按組選擇,則使用者只能檢索"425"、"555"或"0187"字串組。 如果組選擇被禁用,用戶可以檢索電話號碼的整個文本:「(425) 555-0187"。

## <a name="cmfcmaskededitenablesetmaskedcharsonly"></a><a name="enablesetmaskedcharsonly"></a>CMFC蒙面編輯:僅啟用SetSet

指定文本是僅針對蒙版字元驗證的,還是針對整個掩碼驗證的。

```cpp
void EnableSetMaskedCharsOnly(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>參數

*b 啟用*<br/>
[在]TRUE 以僅根據蒙版字元驗證使用者輸入;FALSE 以驗證整個遮罩。 預設值為 TRUE。

## <a name="cmfcmaskededitgetwindowtext"></a><a name="getwindowtext"></a>CMFCSsedit 編輯:抓取視窗文字

從蒙版編輯控件檢索已驗證的文本。

```
int GetWindowText(
    LPTSTR lpszStringBuf,
    int nMaxCount) const;

void GetWindowText(CString& rstrString) const;
```

### <a name="parameters"></a>參數

*lpszStringBuf*<br/>
[出]指向從編輯控制件接收文本的緩衝區的指標。

*nMax( N) Count*<br/>
[在]要接收的最大字元數。

*rstrString*<br/>
[出]對從編輯控制件接收文本的字串物件的引用。

### <a name="return-value"></a>傳回值

第一個方法重載返回複製到*lpszStringBuf*參數緩衝區的字串的位元組數;如果蒙版編輯控件沒有文本,則為 0。

### <a name="remarks"></a>備註

此方法將文字從遮罩編輯控制檔到*lpszStringBuf*緩衝區或*rstrString 字串*。

此方法重新定義[了 CWnd::getWindowText](../../mfc/reference/cwnd-class.md#getwindowtext)。

## <a name="cmfcmaskededitismaskedchar"></a><a name="ismaskedchar"></a>CMFC蒙面編輯::被蒙塞查爾

由框架呼叫,以根據相應的遮罩指定的字元。

```
virtual BOOL IsMaskedChar(
    TCHAR chChar,
    TCHAR chMaskChar) const;
```

### <a name="parameters"></a>參數

*chChar*<br/>
[在]要驗證的字元。

*chMaskChar*<br/>
[在]遮罩字串的字元。

### <a name="return-value"></a>傳回值

如果*chChar*參數是*chMaskChar*參數允許的字元類型,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

重寫此方法以自行驗證輸入字元。 有關蒙版字元的詳細資訊,請參閱[CMFCEdit::啟用掩碼](#enablemask)方法。

## <a name="cmfcmaskededitsetvalidchars"></a><a name="setvalidchars"></a>CMFC 掃描編輯::設定有效字元

指定使用者可以輸入的有效字元字串。

```cpp
void SetValidChars(LPCTSTR lpszValid=NULL);
```

### <a name="parameters"></a>參數

*lpsz 有效*<br/>
[在]包含有效輸入字元集的字串。 NULL 表示所有字元都有效。 此參數的預設值為 NULL。

### <a name="remarks"></a>備註

使用此方法定義有效字元的清單。 如果輸入字元不在此清單中,則遮罩編輯控制項將不接受它。

以下代碼示例僅接受十六進位數位。

```cpp
//Mask: 0xFFFF
m_wndMaskEdit.EnableMask(
    _T(" AAAA"),                // The mask string.
    _T("0x____"),               // The literal template string.
    _T('_'));                   // The default character that
                                // replaces the backspace character.
// Valid string characters
m_wndMaskEdit.SetValidChars(_T("1234567890ABCDEFabcdef"));m_wndMaskEdit.SetWindowText(_T("0x01AF"));
```

## <a name="cmfcmaskededitsetwindowtext"></a><a name="setwindowtext"></a>CMFCSsedit:設定視窗文字

在蒙版編輯控制項中顯示提示。

```cpp
void SetWindowText(LPCTSTR lpszString);
```

### <a name="parameters"></a>參數

*lpszString*<br/>
[在]指向將用作提示的 null 終止字串。

### <a name="remarks"></a>備註

此方法設定控制項文本。

這個方法重新定義[CWnd:setWindowText](../../mfc/reference/cwnd-class.md#setwindowtext)。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)
