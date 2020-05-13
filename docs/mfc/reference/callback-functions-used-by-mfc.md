---
title: MFC 使用的回呼函式
ms.date: 11/04/2016
helpviewer_keywords:
- callback functions [MFC], MFC
- MFC, callback functions
- functions [MFC], callback
- callback functions [MFC]
ms.assetid: b2a6857c-fdd3-45ec-8fd8-2e71fac77582
ms.openlocfilehash: 8d84f939795e768c6b1356dcd8dc291421aedfdc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371130"
---
# <a name="callback-functions-used-by-mfc"></a>MFC 使用的回呼函式

微軟基礎類庫中有三個回調函數。 這些回檔函數傳遞到[CDC::枚舉物件](../../mfc/reference/cdc-class.md#enumobjects)[、CDC::灰色字串](../../mfc/reference/cdc-class.md#graystring)和[CDC::SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc)。 請注意,所有回調函數在返回到 Windows 之前都必須捕獲 MFC 異常,因為異常不能跨回調邊界引發。 有關異常的詳細資訊,請參閱文章["例外](../../mfc/exception-handling-in-mfc.md)"。

|名稱||
|----------|-----------------|
|[CDC::EnumObjects 的回呼函數](#enum_objects)||
|[CDC::GrayString 的回呼函數](#graystring)||
|[CDC::SetAbortProc 的回呼函數](#setabortproc)||

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="callback-function-for-cdcenumobjects"></a><a name="enum_objects"></a>CDC 的回檔函數::枚舉物件

*ObjectFunc*名稱是應用程式提供的函數名稱的占位符。

### <a name="syntax"></a>語法

```
int CALLBACK EXPORT ObjectFunc(
    LPSTR lpszLogObject,
    LPSTR* lpData);
```

### <a name="parameters"></a>參數

*lpszLogObject*<br/>
指向包含有關物件邏輯屬性的資訊的[LOGPEN](/windows/win32/api/Wingdi/ns-wingdi-logpen)或[LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush)資料結構。

*lpData*<br/>
指向傳遞至 `EnumObjects` 函式的應用程式所提供的資料。

### <a name="return-value"></a>傳回值

回檔函數傳**回 int**。此返回的值由使用者定義。 如果回呼函式傳回 0，`EnumObjects` 會及早停止列舉。

### <a name="remarks"></a>備註

必須輸出實際的名稱。

## <a name="callback-function-for-cdcgraystring"></a><a name="graystring"></a>CDC 的回檔函數::灰色字串

*OutputFunc*是應用程式提供的回調函數名稱的占位符。

### <a name="syntax"></a>語法

```
BOOL CALLBACK EXPORT OutputFunc(
    HDC hDC,
    LPARAM lpData,
    int nCount);
```

### <a name="parameters"></a>參數

*hDC*<br/>
標識記憶體設備上下文,其位圖至少為和`nWidth``nHeight`指定的寬度和高度。 `GrayString`

*lpData*<br/>
指向要繪製的字元字串。

*n( N) Count*<br/>
指定要輸出的字元數。

### <a name="return-value"></a>傳回值

回檔函數的返回值必須為 TRUE 才能指示成功;否則,它是FALSE。

### <a name="remarks"></a>備註

回檔函數 *(OutputFunc)* 必須繪製相對於座標 (0,0) 而不是 *(x*, *y*) 的圖像。

## <a name="callback-function-for-cdcsetabortproc"></a><a name="setabortproc"></a>CDC 的回檔功能::SetAbortProc

名稱*AbortFunc*是應用程式提供的函數名稱的占位符。

### <a name="syntax"></a>語法

```
BOOL CALLBACK EXPORT AbortFunc(
    HDC hPr,
    int code);
```

### <a name="parameters"></a>參數

*hPr*<br/>
標識設備上下文。

*代碼*<br/>
指定是否發生了錯誤。 如果未發生錯誤,則為 0。 如果列印管理器當前磁碟空間不足,並且如果應用程式等待,則更多的磁碟空間將變為可用,SP_OUTOFDISK。 如果*代碼*SP_OUTOFDISK,則應用程式不必中止列印作業。 否則,它必須通過調用`PeekMessage`或`GetMessage`Windows函數屈服於列印管理器。

### <a name="return-value"></a>傳回值

如果列印作業要繼續,中止處理程式函數的返回值為非零;如果取消,則返回值為 0。

### <a name="remarks"></a>備註

實際名稱必須匯出,如 CDC 的備註部分[的註:setAbortProc](../../mfc/reference/cdc-class.md#setabortproc)。

## <a name="see-also"></a>另請參閱

[結構、樣式、回呼和訊息對應](structures-styles-callbacks-and-message-maps.md)<br/>
[CDC::枚舉物件](../../mfc/reference/cdc-class.md#enumobjects)<br/>
[CDC::SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc)<br/>
[CDC::灰色字串](../../mfc/reference/cdc-class.md#graystring)
