---
title: MFC 使用的回呼函式
ms.date: 11/04/2016
helpviewer_keywords:
- callback functions [MFC], MFC
- MFC, callback functions
- functions [MFC], callback
- callback functions [MFC]
ms.assetid: b2a6857c-fdd3-45ec-8fd8-2e71fac77582
ms.openlocfilehash: 84581a4a1147a5b0b046e1bf2fbe412bffe9c662
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65612245"
---
# <a name="callback-functions-used-by-mfc"></a>MFC 使用的回呼函式

Microsoft Foundation 類別程式庫中，出現三個回呼函式。 這些回呼函式傳遞至[cdc:: enumobjects](../../mfc/reference/cdc-class.md#enumobjects)， [cdc:: graystring](../../mfc/reference/cdc-class.md#graystring)，並[cdc:: setabortproc](../../mfc/reference/cdc-class.md#setabortproc)。 請注意，所有的回呼函式必須攔截 MFC 例外狀況，然後再回到 Windows，因為無法跨回呼界限擲回例外狀況。 如需例外狀況的詳細資訊，請參閱文章[例外狀況](../../mfc/exception-handling-in-mfc.md)。

|名稱||
|----------|-----------------|
|[CDC::EnumObjects 的回呼函數](#enum_objects)||
|[CDC::GrayString 的回呼函數](#graystring)||
|[CDC::SetAbortProc 的回呼函數](#setabortproc)||

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="enum_objects"></a> Cdc:: enumobjects 的回呼函式

*ObjectFunc*名稱是應用程式提供的函式名稱的預留位置。

### <a name="syntax"></a>語法

```
int CALLBACK EXPORT ObjectFunc(
    LPSTR lpszLogObject,
    LPSTR* lpData);
```

### <a name="parameters"></a>參數

*lpszLogObject*<br/>
指向[LOGPEN](/windows/desktop/api/Wingdi/ns-wingdi-taglogpen)或是[LOGBRUSH](/windows/desktop/api/wingdi/ns-wingdi-taglogbrush)資料結構，包含物件的邏輯屬性相關資訊。

*lpData*<br/>
指向傳遞至 `EnumObjects` 函式的應用程式所提供的資料。

### <a name="return-value"></a>傳回值

回呼函式會傳回**int**。這個傳回的值是使用者定義的。 如果回呼函式傳回 0，`EnumObjects` 會及早停止列舉。

### <a name="remarks"></a>備註

必須輸出實際的名稱。

## <a name="graystring"></a>  Cdc:: graystring 的回呼函式

*OutputFunc*是應用程式所提供的回呼函式名稱的預留位置。

### <a name="syntax"></a>語法

```
BOOL CALLBACK EXPORT OutputFunc(
    HDC hDC,
    LPARAM lpData,
    int nCount);
```

### <a name="parameters"></a>參數

*hDC*<br/>
識別記憶體裝置內容的最少的點陣圖寬度和高度所指定`nWidth`並`nHeight`至`GrayString`。

*lpData*<br/>
指向要繪製的字元字串。

*nCount*<br/>
指定要輸出的字元數。

### <a name="return-value"></a>傳回值

回呼函式的傳回值必須是 TRUE，表示作業成功;否則，它會是 FALSE。

### <a name="remarks"></a>備註

回呼函式 (*OutputFunc*) 必須繪製影像相對於座標 (0，0) 而非 (*x*， *y*)。

## <a name="setabortproc"></a>  Cdc:: setabortproc 的回呼函式

名稱*AbortFunc*是應用程式提供的函式名稱的預留位置。

### <a name="syntax"></a>語法

```
BOOL CALLBACK EXPORT AbortFunc(
    HDC hPr,
    int code);
```

### <a name="parameters"></a>參數

*hPr*<br/>
識別裝置內容。

*程式碼*<br/>
指定是否已發生錯誤。 如果沒有發生任何錯誤，它就會是 0。 它時 SP_OUTOFDISK 如果列印管理員目前的磁碟空間和更多磁碟空間的可用應用程式會等候。 如果*程式碼*是 SP_OUTOFDISK，應用程式不需要中止列印工作。 如果不存在，它必須產生列印管理員藉由呼叫`PeekMessage`或`GetMessage`Windows 函式。

### <a name="return-value"></a>傳回值

中止處理常式函式的傳回值為非零值，若要繼續，列印工作是否和 0 如果它已取消。

### <a name="remarks"></a>備註

必須匯出的實際名稱，如 < 備註 > 一節中所述[cdc:: setabortproc](../../mfc/reference/cdc-class.md#setabortproc)。

## <a name="see-also"></a>另請參閱

[結構、樣式、回呼和訊息對應](structures-styles-callbacks-and-message-maps.md)<br/>
[CDC::EnumObjects](../../mfc/reference/cdc-class.md#enumobjects)<br/>
[CDC::SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc)<br/>
[CDC::GrayString](../../mfc/reference/cdc-class.md#graystring)
