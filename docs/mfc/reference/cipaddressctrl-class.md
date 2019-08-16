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
ms.openlocfilehash: fe8e3109b110c27ab32dc1a4f9a132f1e1c18638
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505821"
---
# <a name="cipaddressctrl-class"></a>CIPAddressCtrl 類別

提供 Windows 通用 IP 位址控制項的功能。

## <a name="syntax"></a>語法

```
class CIPAddressCtrl : public CWnd
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CIPAddressCtrl::CIPAddressCtrl](#cipaddressctrl)|建構 `CIPAddressCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CIPAddressCtrl::ClearAddress](#clearaddress)|清除 IP 位址控制項的內容。|
|[CIPAddressCtrl::Create](#create)|建立 IP 位址控制項, 並將它附加至`CIPAddressCtrl`物件。|
|[CIPAddressCtrl::CreateEx](#createex)|使用指定的 Windows 擴充樣式建立 IP 位址控制項, 並將其附加至`CIPAddressCtrl`物件。|
|[CIPAddressCtrl::GetAddress](#getaddress)|抓取 IP 位址控制中所有四個欄位的位址值。|
|[CIPAddressCtrl::IsBlank](#isblank)|判斷 IP 位址控制項中的所有欄位是否都是空的。|
|[CIPAddressCtrl::SetAddress](#setaddress)|設定 IP 位址控制中所有四個欄位的位址值。|
|[CIPAddressCtrl::SetFieldFocus](#setfieldfocus)|將鍵盤焦點設定為 IP 位址控制中的指定欄位。|
|[CIPAddressCtrl::SetFieldRange](#setfieldrange)|設定 IP 位址控制中指定欄位內的範圍。|

## <a name="remarks"></a>備註

IP 位址控制 (類似于編輯控制項的控制項) 可讓您輸入和操作網際網路通訊協定 (IP) 格式的數位位址。

這個控制項 (因此`CIPAddressCtrl`類別) 僅適用于在 Microsoft Internet Explorer 4.0 和更新版本下執行的程式。 未來的 Windows 和 Windows NT 版本也會提供這些功能。

如需有關 IP 位址控制的一般資訊, 請參閱 Windows SDK 中的[Ip 位址控制項](/windows/win32/Controls/ip-address-controls)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CIPAddressCtrl`

## <a name="requirements"></a>需求

**標頭：** afxcmn.h

##  <a name="cipaddressctrl"></a>  CIPAddressCtrl::CIPAddressCtrl

建立 `CIPAddressCtrl` 物件。

```
CIPAddressCtrl();
```

##  <a name="clearaddress"></a>  CIPAddressCtrl::ClearAddress

清除 IP 位址控制項的內容。

```
void ClearAddress();
```

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [IPM_CLEARADDRESS](/windows/win32/Controls/ipm-clearaddress)的行為, 如 Windows SDK 中所述。

##  <a name="create"></a>  CIPAddressCtrl::Create

建立 IP 位址控制項, 並將它附加至`CIPAddressCtrl`物件。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
IP 位址控制項的樣式。 套用視窗樣式的組合。 您必須包含 WS_CHILD 樣式, 因為控制項必須是子視窗。 如需 Windows 樣式的清單, 請參閱 Windows SDK 中的[CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) 。

*rect*<br/>
IP 位址控制項的大小和位置的參考。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](/previous-versions/dd162897\(v=vs.85\))結構。

*pParentWnd*<br/>
IP 位址控制項的父視窗指標。 不得為 Null。

*nID*<br/>
IP 位址控制項的識別碼。

### <a name="return-value"></a>傳回值

如果初始化成功, 則為非零;否則為0。

### <a name="remarks"></a>備註

您可以使用`CIPAddressCtrl`兩個步驟來建立物件。

1. 呼叫會建立`CIPAddressCtrl`物件的函式。

1. 呼叫`Create`, 它會建立 IP 位址控制項。

如果您想要搭配控制項使用擴充的 windows 樣式, 請呼叫[CreateEx](#createex) , `Create`而不是。

##  <a name="createex"></a>  CIPAddressCtrl::CreateEx

呼叫這個函式以建立控制項 (子視窗), 並將它與`CIPAddressCtrl`物件產生關聯。

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
指定所要建立之控制項的延伸樣式。 如需擴充 Windows 樣式的清單, 請參閱 Windows SDK 中[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的*dwExStyle*參數。

*dwStyle*<br/>
IP 位址控制項的樣式。 套用視窗樣式的組合。 您必須包含 WS_CHILD 樣式, 因為控制項必須是子視窗。 如需 Windows 樣式的清單, 請參閱 Windows SDK 中的[CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) 。

*rect*<br/>
[矩形](/previous-versions/dd162897\(v=vs.85\))結構的參考, 描述要建立之視窗的大小和位置, 以*pParentWnd*的用戶端座標表示。

*pParentWnd*<br/>
做為控制項父系之視窗的指標。

*nID*<br/>
控制項的子視窗識別碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

使用`CreateEx` , 而不是[Create](#create)來套用擴充的 windows 樣式 (由 Windows 擴充樣式指定于**WS_EX_** 的前面)。

##  <a name="getaddress"></a>  CIPAddressCtrl::GetAddress

抓取 IP 位址控制中所有四個欄位的位址值。

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
來自已封裝 IP 位址之欄位0值的參考。

*nField1*<br/>
來自已封裝 IP 位址之欄位1值的參考。

*nField2*<br/>
來自已封裝 IP 位址之欄位2值的參考。

*nField3*<br/>
來自已封裝 IP 位址之欄位3值的參考。

*dwAddress*<br/>
接收 IP 位址的 DWORD 值之位址的參考。 如需顯示如何填滿*dwAddress*的表格, 請參閱**備註**。

### <a name="return-value"></a>傳回值

IP 位址控制中非空白欄位的數目。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [IPM_GETADDRESS](/windows/win32/Controls/ipm-getaddress)的行為, 如 Windows SDK 中所述。 在上述的第一個原型中, 控制項的欄位0到3中的數位會分別由左至右讀取, 以填入四個參數。 在上述的第二個原型中, *dwAddress*的填入方式如下。

|欄位|包含域值的位|
|-----------|-------------------------------------|
|0|24到31|
|1|16到23|
|2|8至15|
|3|0到7|

##  <a name="isblank"></a>CIPAddressCtrl:: IsBlank

判斷 IP 位址控制項中的所有欄位是否都是空的。

```
BOOL IsBlank() const;
```

### <a name="return-value"></a>傳回值

如果所有 IP 位址控制欄位都是空的, 則為非零。否則為0。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [IPM_ISBLANK](/windows/win32/Controls/ipm-isblank)的行為, 如 Windows SDK 中所述。

##  <a name="setaddress"></a>  CIPAddressCtrl::SetAddress

設定 IP 位址控制中所有四個欄位的位址值。

```
void SetAddress(
    BYTE nField0,
    BYTE nField1,
    BYTE nField2,
    BYTE nField3);

void SetAddress(DWORD dwAddress);
```

### <a name="parameters"></a>參數

*nField0*<br/>
來自已封裝 IP 位址的欄位0值。

*nField1*<br/>
來自已封裝 IP 位址的欄位1值。

*nField2*<br/>
來自已封裝 IP 位址的欄位2值。

*nField3*<br/>
來自已封裝 IP 位址的欄位3值。

*dwAddress*<br/>
DWORD 值, 其中包含新的 IP 位址。 如需顯示如何填滿 DWORD 值的資料表, 請參閱**備註**。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [IPM_SETADDRESS](/windows/win32/Controls/ipm-setaddress)的行為, 如 Windows SDK 中所述。 在上述的第一個原型中, 控制項的欄位0到3中的數位會分別由左至右讀取, 以填入四個參數。 在上述的第二個原型中, *dwAddress*的填入方式如下。

|欄位|包含域值的位|
|-----------|-------------------------------------|
|0|24到31|
|1|16到23|
|2|8至15|
|3|0到7|

##  <a name="setfieldfocus"></a>CIPAddressCtrl::SetFieldFocus

將鍵盤焦點設定為 IP 位址控制中的指定欄位。

```
void SetFieldFocus(WORD nField);
```

### <a name="parameters"></a>參數

*nField*<br/>
應設定焦點之以零為起始的欄位索引。 如果這個值大於欄位數目, 焦點就會設為第一個空白欄位。 如果所有欄位都不是空白, 則焦點會設定為第一個欄位。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [IPM_SETFOCUS](/windows/win32/Controls/ipm-setfocus)的行為, 如 Windows SDK 中所述。

##  <a name="setfieldrange"></a>CIPAddressCtrl::SetFieldRange

設定 IP 位址控制中指定欄位內的範圍。

```
void SetFieldRange(
    int nField,
    BYTE nLower,
    BYTE nUpper);
```

### <a name="parameters"></a>參數

*nField*<br/>
以零為基底的欄位索引, 將套用範圍。

*nLower*<br/>
在此 IP 位址控制中, 接收指定欄位之下限的整數參考。

*nUpper*<br/>
在此 IP 位址控制中, 接收指定欄位上限的整數參考。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [IPM_SETRANGE](/windows/win32/Controls/ipm-setrange)的行為, 如 Windows SDK 中所述。 使用*nLower*和*nUpper*這兩個參數, 表示欄位的下限和上限, 而不是與 Win32 訊息搭配使用的*wRange*參數。

## <a name="see-also"></a>另請參閱

[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
