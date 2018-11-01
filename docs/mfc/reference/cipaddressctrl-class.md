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
ms.openlocfilehash: fe5503eb78954bf39a135cd0e4acda6c37fc5fa9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50568697"
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
|[CIPAddressCtrl::CIPAddressCtrl](#cipaddressctrl)|建構 `CIPAddressCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CIPAddressCtrl::ClearAddress](#clearaddress)|清除 IP 位址控制項的內容。|
|[CIPAddressCtrl::Create](#create)|建立 IP 位址控制項，並將它附加至`CIPAddressCtrl`物件。|
|[CIPAddressCtrl::CreateEx](#createex)|使用指定的 Windows 延伸樣式建立的 IP 位址控制項，並將它附加至`CIPAddressCtrl`物件。|
|[CIPAddressCtrl::GetAddress](#getaddress)|擷取 IP 位址控制項中的所有四個欄位的位址值。|
|[CIPAddressCtrl::IsBlank](#isblank)|判斷 IP 位址控制項中的所有欄位都是否空白。|
|[CIPAddressCtrl::SetAddress](#setaddress)|設定 IP 位址控制項中的所有四個欄位的位址值。|
|[CIPAddressCtrl::SetFieldFocus](#setfieldfocus)|將鍵盤焦點設定為 IP 位址控制項中的指定欄位。|
|[CIPAddressCtrl::SetFieldRange](#setfieldrange)|在 IP 位址控制項中指定的欄位會設定範圍。|

## <a name="remarks"></a>備註

為 IP 位址控制項，類似於編輯控制項，控制項可讓您輸入及管理以網際網路通訊協定 (IP) 格式的數值位址。

這個控制項 (並因此`CIPAddressCtrl`類別) 僅適用於在 Microsoft Internet Explorer 4.0 和更新版本執行的程式。 它們也可在未來的版本的 Windows 和 Windows NT。

更多一般 IP 位址控制項的詳細資訊，請參閱[IP 位址控制項](/windows/desktop/Controls/ip-address-controls)Windows SDK 中。

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

此成員函式實作的 Win32 訊息的行為[IPM_CLEARADDRESS](/windows/desktop/Controls/ipm-clearaddress)、 Windows SDK 中所述。

##  <a name="create"></a>  CIPAddressCtrl::Create

建立 IP 位址控制項，並將它附加至`CIPAddressCtrl`物件。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*cheaderctrl:: Create*<br/>
IP 位址控制項的樣式。 套用視窗樣式的組合。 因為控制項必須是子視窗，您必須包含 WS_CHILD 樣式。 請參閱[CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa) Windows sdk for windows 樣式的清單。

*rect*<br/>
IP 位址控制項的大小和位置參考。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)結構。

*pParentWnd*<br/>
IP 位址控制項的父視窗的指標。 它必須不是 NULL。

*nID*<br/>
IP 位址控制項的 id。

### <a name="return-value"></a>傳回值

非零值，如果初始化成功;否則為 0。

### <a name="remarks"></a>備註

您建構`CIPAddressCtrl`兩個步驟中的物件。

1. 呼叫建構函式，這會建立`CIPAddressCtrl`物件。

1. 呼叫`Create`，這會建立 IP 位址控制項。

如果您想要使用擴充的 windows 樣式和控制項，呼叫[CreateEx](#createex)而不是`Create`。

##  <a name="createex"></a>  CIPAddressCtrl::CreateEx

呼叫此函式來建立控制項 （子視窗），但其關聯`CIPAddressCtrl`物件。

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
指定正在建立之控制項的延伸的樣式。 如需延伸的 Windows 樣式的清單，請參閱 < *dwExStyle*參數[CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) Windows SDK 中。

*cheaderctrl:: Create*<br/>
IP 位址控制項的樣式。 套用視窗樣式的組合。 因為控制項必須是子視窗，您必須包含 WS_CHILD 樣式。 請參閱[CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa) Windows sdk for windows 樣式的清單。

*rect*<br/>
參考[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)結構描述的大小和位置，在中建立工作區座標中的視窗*pParentWnd*。

*pParentWnd*<br/>
是控制項的父視窗的指標。

*nID*<br/>
控制項的子視窗識別碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

使用`CreateEx`而非[建立](#create)套用延伸的 Windows 樣式，由 Windows 延伸的樣式前置詞**WS_EX_**。

##  <a name="getaddress"></a>  CIPAddressCtrl::GetAddress

擷取 IP 位址控制項中的所有四個欄位的位址值。

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
從壓縮的 IP 位址欄位 0 值參考。

*nField1*<br/>
從壓縮的 IP 位址欄位 1 值參考。

*nField2*<br/>
從壓縮的 IP 位址欄位 2 值參考。

*nField3*<br/>
從壓縮的 IP 位址欄位 3 值參考。

*dwAddress*<br/>
接收的 IP 位址的 DWORD 值的位址參考。 請參閱**備註**的資料表，其中顯示如何*dwAddress*填滿。

### <a name="return-value"></a>傳回值

在 IP 位址控制項中的非空白欄位數目。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[IPM_GETADDRESS](/windows/desktop/Controls/ipm-getaddress)、 Windows SDK 中所述。 在上述第一個原型，讀取欄位 0 到 3 的控制項中的數字由左到右分別，填入的四個參數。 在上述的第二個原型*dwAddress*已填入，如下所示。

|欄位|包含欄位值的位元|
|-----------|-------------------------------------|
|0|24 到 31|
|1|16 到 23|
|2|8 到 15|
|3|0 到 7|

##  <a name="isblank"></a>  CIPAddressCtrl::IsBlank

判斷 IP 位址控制項中的所有欄位都是否空白。

```
BOOL IsBlank() const;
```

### <a name="return-value"></a>傳回值

如果所有的 IP 位址控制項欄位是空的則為非零否則為 0。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[IPM_ISBLANK](/windows/desktop/Controls/ipm-isblank)、 Windows SDK 中所述。

##  <a name="setaddress"></a>  CIPAddressCtrl::SetAddress

設定 IP 位址控制項中的所有四個欄位的位址值。

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
從壓縮的 IP 位址欄位 0 值。

*nField1*<br/>
從壓縮的 IP 位址欄位 1 值。

*nField2*<br/>
從壓縮的 IP 位址欄位 2 值。

*nField3*<br/>
從壓縮的 IP 位址欄位 3 值。

*dwAddress*<br/>
包含新的 IP 位址的 DWORD 值。 請參閱**備註**如何填滿的 DWORD 值會顯示為資料表。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[IPM_SETADDRESS](/windows/desktop/Controls/ipm-setaddress)、 Windows SDK 中所述。 在上述第一個原型，讀取欄位 0 到 3 的控制項中的數字由左到右分別，填入的四個參數。 在上述的第二個原型*dwAddress*已填入，如下所示。

|欄位|包含欄位值的位元|
|-----------|-------------------------------------|
|0|24 到 31|
|1|16 到 23|
|2|8 到 15|
|3|0 到 7|

##  <a name="setfieldfocus"></a>  CIPAddressCtrl::SetFieldFocus

將鍵盤焦點設定為 IP 位址控制項中的指定欄位。

```
void SetFieldFocus(WORD nField);
```

### <a name="parameters"></a>參數

*nField*<br/>
以零為起始的欄位應該設定焦點的索引。 如果此值大於欄位數目，會將焦點設的第一個空白欄位。 如果所有的欄位是 非空白，會將焦點設第一個欄位。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[IPM_SETFOCUS](/windows/desktop/Controls/ipm-setfocus)、 Windows SDK 中所述。

##  <a name="setfieldrange"></a>  CIPAddressCtrl::SetFieldRange

在 IP 位址控制項中指定的欄位會設定範圍。

```
void SetFieldRange(
    int nField,
    BYTE nLower,
    BYTE nUpper);
```

### <a name="parameters"></a>參數

*nField*<br/>
將套用該範圍的以零為起始的欄位索引。

*nLower*<br/>
在此 IP 位址控制項中接收指定之欄位的下限的整數參考。

*nUpper*<br/>
在此 IP 位址控制項中接收指定之欄位的上限的整數參考。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[IPM_SETRANGE](/windows/desktop/Controls/ipm-setrange)、 Windows SDK 中所述。 您可以使用兩個參數， *nLower*並*nUpper*，以指出的下限和上限的限制和欄位，而不是*wRange*參數搭配的 Win32 訊息。

## <a name="see-also"></a>另請參閱

[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)

