---
title: MFC 使用的回呼函式
ms.date: 11/04/2016
helpviewer_keywords:
- callback functions [MFC], MFC
- MFC, callback functions
- functions [MFC], callback
- callback functions [MFC]
ms.assetid: b2a6857c-fdd3-45ec-8fd8-2e71fac77582
ms.openlocfilehash: 553e87320828590c9e1e9204b54622f2f1ca6d80
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040882"
---
# <a name="callback-functions-used-by-mfc"></a>MFC 使用的回呼函式

MFC 程式庫中出現三個回呼函數。 這些回呼函數會傳遞至 [cdc：： EnumObjects](../../mfc/reference/cdc-class.md#enumobjects)、 [Cdc：： GrayString](../../mfc/reference/cdc-class.md#graystring)和 [cdc：： SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc)。 請注意，所有回呼函式必須先攔截 MFC 例外狀況，然後再返回 Windows，因為無法跨回呼界限擲回例外狀況。 如需例外狀況的詳細資訊，請參閱文章 [例外](../../mfc/exception-handling-in-mfc.md)狀況。

[CDC：： EnumObjects 的回呼函數](#enum_objects)\
[CDC：： GrayString 的回呼函數](#graystring)\
[CDC::SetAbortProc 的回呼函數](#setabortproc)

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="callback-function-for-cdcenumobjects"></a><a name="enum_objects"></a> CDC：： EnumObjects 的回呼函數

*ObjectFunc*名稱是應用程式提供之函式名稱的預留位置。

### <a name="syntax"></a>語法

```
int CALLBACK EXPORT ObjectFunc(
    LPSTR lpszLogObject,
    LPSTR* lpData);
```

### <a name="parameters"></a>參數

*lpszLogObject*<br/>
指向 [LOGPEN](/windows/win32/api/Wingdi/ns-wingdi-logpen) 或 [LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush) 資料結構，其中包含物件之邏輯屬性的相關資訊。

*lpData*<br/>
指向傳遞至 `EnumObjects` 函式的應用程式所提供的資料。

### <a name="return-value"></a>傳回值

回呼函數會傳回 **`int`** 。 這個傳回的值是使用者定義的。 如果回呼函式傳回 0，`EnumObjects` 會及早停止列舉。

### <a name="remarks"></a>備註

必須輸出實際的名稱。

## <a name="callback-function-for-cdcgraystring"></a><a name="graystring"></a> CDC：： GrayString 的回呼函數

*OutputFunc* 是應用程式提供之回呼函數名稱的預留位置。

### <a name="syntax"></a>語法

```
BOOL CALLBACK EXPORT OutputFunc(
    HDC hDC,
    LPARAM lpData,
    int nCount);
```

### <a name="parameters"></a>參數

*hDC*<br/>
識別至少具有和所指定之寬度和高度之點陣圖的記憶體裝置內容 `nWidth` `nHeight` `GrayString` 。

*lpData*<br/>
指向要繪製的字元字串。

*nCount*<br/>
指定要輸出的字元數目。

### <a name="return-value"></a>傳回值

回呼函式的傳回值必須為 TRUE，才能表示成功;否則為 FALSE。

### <a name="remarks"></a>備註

回呼函數 (*OutputFunc*) 必須繪製相對於座標的影像 (0、0) 而不是 (*x*， *y*) 。

## <a name="callback-function-for-cdcsetabortproc"></a><a name="setabortproc"></a> CDC：： SetAbortProc 的回呼函數

名稱 *AbortFunc* 是應用程式提供之函式名稱的預留位置。

### <a name="syntax"></a>語法

```
BOOL CALLBACK EXPORT AbortFunc(
    HDC hPr,
    int code);
```

### <a name="parameters"></a>參數

*hPr*<br/>
識別裝置內容。

*code*<br/>
指定是否發生錯誤。 如果未發生任何錯誤，則為0。 如果列印管理員目前的磁碟空間不足，且如果應用程式等候時有更多的磁碟空間可供使用，就會 SP_OUTOFDISK。 如果 SP_OUTOFDISK 程式 *代碼* ，則應用程式不需要中止列印工作。 如果不是，則必須藉由呼叫或 Windows 函式來產生列印管理員 `PeekMessage` `GetMessage` 。

### <a name="return-value"></a>傳回值

如果列印工作要繼續，則 abort 處理常式函式的傳回值為非零值，如果已取消，則為0。

### <a name="remarks"></a>備註

實際的名稱必須如 [CDC：： SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc)的「備註」一節所述匯出。

## <a name="see-also"></a>另請參閱

[結構、樣式、回呼和訊息對應](structures-styles-callbacks-and-message-maps.md)<br/>
[CDC：： EnumObjects](../../mfc/reference/cdc-class.md#enumobjects)<br/>
[CDC：： SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc)<br/>
[CDC：： GrayString](../../mfc/reference/cdc-class.md#graystring)
