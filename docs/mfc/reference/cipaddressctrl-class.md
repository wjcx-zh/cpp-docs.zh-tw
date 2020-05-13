---
title: CIPAddressCtrl 類別
ms.date: 11/04/2016
f1_keywords:
- CIPAddressCtrl
- AFXCMN/CIPAddressCtrl
- AFXCMN/CIPAddressCtrl::CIPAddressCtrl
- AFXCMN/CIPAddressCtrl::ClearAddress
- AFXCMN/CIPAddressCtrl::Create
- AFXCMN/CIPAddressCtrl::CreateEx
- AFXCMN/CIPAddressCtrl::GetAddress
- AFXCMN/CIPAddressCtrl::IsBlank
- AFXCMN/CIPAddressCtrl::SetAddress
- AFXCMN/CIPAddressCtrl::SetFieldFocus
- AFXCMN/CIPAddressCtrl::SetFieldRange
helpviewer_keywords:
- CIPAddressCtrl [MFC], CIPAddressCtrl
- CIPAddressCtrl [MFC], ClearAddress
- CIPAddressCtrl [MFC], Create
- CIPAddressCtrl [MFC], CreateEx
- CIPAddressCtrl [MFC], GetAddress
- CIPAddressCtrl [MFC], IsBlank
- CIPAddressCtrl [MFC], SetAddress
- CIPAddressCtrl [MFC], SetFieldFocus
- CIPAddressCtrl [MFC], SetFieldRange
ms.assetid: 9764d2f4-cb14-4ba8-b799-7f57a55a47c6
ms.openlocfilehash: 0613dea766b022acf140a82bb4b01784793c2589
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754958"
---
# <a name="cipaddressctrl-class"></a>CIPAddressCtrl 類別

提供 Windows 通用 IP 位址控制項的功能。

## <a name="syntax"></a>語法

```
class CIPAddressCtrl : public CWnd
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CIPAddressCtrl:CIPAddressCtrl](#cipaddressctrl)|建構 `CIPAddressCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CIP位址::清除位址](#clearaddress)|清除 IP 位址控制件的內容。|
|[CIP位址Ctrl:建立](#create)|創建 IP 位址控制檔並將其`CIPAddressCtrl`附加到 物件。|
|[CIP位址Ctrl:建立Ex](#createex)|使用指定的 Windows 擴充樣式創建 IP 位址控制項`CIPAddressCtrl`,並將其附加到 物件。|
|[CIP位址::取得位址](#getaddress)|檢索 IP 位址控制件中所有四個字段的位址值。|
|[CIP位址::是空白](#isblank)|確定 IP 位址控制件中的所有欄位是否為空。|
|[CIP位址::設定位址](#setaddress)|設置 IP 位址控制項中所有四個字段的位址值。|
|[CIPAddressCtrl::集場焦點](#setfieldfocus)|將鍵盤焦點設定到 IP 位址控制檔中的指定欄位。|
|[CIPAddressCtrl::塞特菲爾德](#setfieldrange)|設置 IP 位址控制項中指定欄位中的範圍。|

## <a name="remarks"></a>備註

IP 位址控制項(類似於編輯控制項)允許您輸入和操作 Internet 協定 (IP) 格式的數位位址。

此控制項(因此是`CIPAddressCtrl`類)僅適用於在 Microsoft Internet Explorer 4.0 和更高版本下運行的程式。 它們也將在未來版本的 Windows 和 Windows NT 下提供。

有關 IP 位址控制檔的更多一般資訊,請參考 Windows SDK 中的[IP 位址控制件](/windows/win32/Controls/ip-address-controls)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CIPAddressCtrl`

## <a name="requirements"></a>需求

**標頭：** afxcmn.h

## <a name="cipaddressctrlcipaddressctrl"></a><a name="cipaddressctrl"></a>CIPAddressCtrl:CIPAddressCtrl

建立 `CIPAddressCtrl` 物件。

```
CIPAddressCtrl();
```

## <a name="cipaddressctrlclearaddress"></a><a name="clearaddress"></a>CIP位址::清除位址

清除 IP 位址控制件的內容。

```cpp
void ClearAddress();
```

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[的行為IPM_CLEARADDRESS](/windows/win32/Controls/ipm-clearaddress),如 Windows SDK 中所述。

## <a name="cipaddressctrlcreate"></a><a name="create"></a>CIP位址Ctrl:建立

創建 IP 位址控制檔並將其`CIPAddressCtrl`附加到 物件。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
IP 位址控制項樣式。 應用視窗樣式的組合。 您必須包括WS_CHILD樣式,因為控件必須是子視窗。 有關視窗樣式的清單,請參閱 Windows SDK 建立[視窗](/windows/win32/api/winuser/nf-winuser-createwindoww)。

*矩形*<br/>
對 IP 位址控制的大小和位置的引用。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](/windows/win32/api/windef/ns-windef-rect)結構。

*pparentwnd*<br/>
指向 IP 位址控制的父視窗的指標。 它不得為 NULL。

*nID*<br/>
IP 位址控制項的識別碼。

### <a name="return-value"></a>傳回值

初始化成功時非零;否則 0。

### <a name="remarks"></a>備註

分兩步`CIPAddressCtrl`構造物件。

1. 調用構造函數,該構造函數創建`CIPAddressCtrl`物件。

1. 呼叫`Create`,它創建 IP 位址控制項。

如果要將延伸視窗樣式與控制項一起使用,請呼叫[CreateEx](#createex)`Create`而不是 。

## <a name="cipaddressctrlcreateex"></a><a name="createex"></a>CIP位址Ctrl:建立Ex

呼叫此函數以建立控制項(子視窗),並將其與`CIPAddressCtrl`物件關聯。

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwExStyle*<br/>
指定要創建的控制項的擴充樣式。 有關擴展 Windows 樣式的清單,請參閱 Windows SDK 中[創建 WindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的*dwExStyle*參數。

*dwStyle*<br/>
IP 位址控制項樣式。 應用視窗樣式的組合。 您必須包括WS_CHILD樣式,因為控件必須是子視窗。 有關視窗樣式的清單,請參閱 Windows SDK 建立[視窗](/windows/win32/api/winuser/nf-winuser-createwindoww)。

*矩形*<br/>
對[RECT](/windows/win32/api/windef/ns-windef-rect)結構的引用,描述要創建的視窗的大小和位置,在*pParentWnd*的用戶端座標中。

*pparentwnd*<br/>
指向控件的父視窗的指標。

*nID*<br/>
控制項的子視窗 ID。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

使用`CreateEx`而不是[「創建](#create)」來應用擴展的 Windows 樣式,該樣式由 Windows 擴充樣式前言**WS_EX_** 指定。

## <a name="cipaddressctrlgetaddress"></a><a name="getaddress"></a>CIP位址::取得位址

檢索 IP 位址控制件中所有四個字段的位址值。

```
int GetAddress(
    BYTE& nField0,
    BYTE& nField1,
    BYTE& nField2,
    BYTE& nField3);

int GetAddress(DWORD& dwAddress);
```

### <a name="parameters"></a>參數

*nField0*<br/>
從打包的 IP 位址對欄位 0 值的引用。

*nField1*<br/>
從打包的 IP 位址對欄位 1 值的引用。

*nField2*<br/>
從打包的 IP 位址對欄位 2 值的引用。

*nField3*<br/>
從打包的 IP 位址對欄位 3 值的引用。

*dwAddress*<br/>
對接收 IP 位址的 DWORD 值位址的引用。 請參考*dwAddress*的表**註 。**

### <a name="return-value"></a>傳回值

IP 位址控制項中的非空白欄位數。

### <a name="remarks"></a>備註

此成員函數實現 win32 消息[IPM_GETADDRESS](/windows/win32/Controls/ipm-getaddress)的行為,如Windows SDK中所述。 在上面的第一個原型中,控件的欄位 0 到 3 中的數位分別從左至右讀取,填充四個參數。 在上面的第二個原型中 *,dwAddress*填充如下。

|欄位|引入欄位值的位元|
|-----------|-------------------------------------|
|0|24 到 31|
|1|16 到 23|
|2|8 到 15|
|3|0 到 7|

## <a name="cipaddressctrlisblank"></a><a name="isblank"></a>CIP位址::是空白

確定 IP 位址控制件中的所有欄位是否為空。

```
BOOL IsBlank() const;
```

### <a name="return-value"></a>傳回值

如果所有 IP 位址控制欄位都為空,則非零;否則 0。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[IPM_ISBLANK](/windows/win32/Controls/ipm-isblank)的行為,如 Windows SDK 中所述。

## <a name="cipaddressctrlsetaddress"></a><a name="setaddress"></a>CIP位址::設定位址

設置 IP 位址控制項中所有四個字段的位址值。

```cpp
void SetAddress(
    BYTE nField0,
    BYTE nField1,
    BYTE nField2,
    BYTE nField3);

void SetAddress(DWORD dwAddress);
```

### <a name="parameters"></a>參數

*nField0*<br/>
來自打包 IP 位址的欄位 0 值。

*nField1*<br/>
來自打包 IP 位址的欄位 1 值。

*nField2*<br/>
包裝 IP 位址中的欄位 2 值。

*nField3*<br/>
來自打包 IP 位址的欄位 3 值。

*dwAddress*<br/>
包含新 IP 位址的 DWORD 值。 請參考顯示如何填充 DWORD 值的表**註**。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[IPM_SETADDRESS](/windows/win32/Controls/ipm-setaddress)的行為,如 Windows SDK 中所述。 在上面的第一個原型中,控件的欄位 0 到 3 中的數位分別從左至右讀取,填充四個參數。 在上面的第二個原型中 *,dwAddress*填充如下。

|欄位|引入欄位值的位元|
|-----------|-------------------------------------|
|0|24 到 31|
|1|16 到 23|
|2|8 到 15|
|3|0 到 7|

## <a name="cipaddressctrlsetfieldfocus"></a><a name="setfieldfocus"></a>CIPAddressCtrl::集場焦點

將鍵盤焦點設定到 IP 位址控制檔中的指定欄位。

```cpp
void SetFieldFocus(WORD nField);
```

### <a name="parameters"></a>參數

*n菲爾德*<br/>
應設置焦點的零基欄位索引。 如果此值大於欄位數,則焦點將設置為第一個空白欄位。 如果所有欄位均為非空白,則焦點將設置為第一個字段。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[IPM_SETFOCUS](/windows/win32/Controls/ipm-setfocus)的行為,如 Windows SDK 中所述。

## <a name="cipaddressctrlsetfieldrange"></a><a name="setfieldrange"></a>CIPAddressCtrl::塞特菲爾德

設置 IP 位址控制項中指定欄位中的範圍。

```cpp
void SetFieldRange(
    int nField,
    BYTE nLower,
    BYTE nUpper);
```

### <a name="parameters"></a>參數

*n菲爾德*<br/>
將應用範圍的零欄位索引。

*n 更低*<br/>
對在此 IP 位址控制件中接收指定欄位的下限的整數的引用。

*n*<br/>
對在此 IP 位址控制件中接收指定欄位上限的整數的引用。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[IPM_SETRANGE](/windows/win32/Controls/ipm-setrange)的行為,如 Windows SDK 中所述。 使用兩個參數*nLower*和*nUpper*來指示欄位的下限和上限,而不是與 Win32 消息一起使用的*wRange*參數。

## <a name="see-also"></a>另請參閱

[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
