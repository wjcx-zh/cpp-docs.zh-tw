---
title: CMetaFileDC 類別
ms.date: 11/04/2016
f1_keywords:
- CMetaFileDC
- AFXEXT/CMetaFileDC
- AFXEXT/CMetaFileDC::CMetaFileDC
- AFXEXT/CMetaFileDC::Close
- AFXEXT/CMetaFileDC::CloseEnhanced
- AFXEXT/CMetaFileDC::Create
- AFXEXT/CMetaFileDC::CreateEnhanced
helpviewer_keywords:
- CMetaFileDC [MFC], CMetaFileDC
- CMetaFileDC [MFC], Close
- CMetaFileDC [MFC], CloseEnhanced
- CMetaFileDC [MFC], Create
- CMetaFileDC [MFC], CreateEnhanced
ms.assetid: ffce60fa-4181-4d46-9832-25e46fad4db4
ms.openlocfilehash: 0919dacfd758df39064c5381690e9e23a029fcd1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369954"
---
# <a name="cmetafiledc-class"></a>CMetaFileDC 類別

實作 Windows 中繼檔，這個檔案包含一連串可重新執行來建立所需影像或文字的繪圖裝置介面 (GDI) 命令。

## <a name="syntax"></a>語法

```
class CMetaFileDC : public CDC
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMetaFileDC:CMetaFileDC](#cmetafiledc)|建構 `CMetaFileDC` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMetaFileDC:關閉](#close)|關閉設備上下文並創建元檔句柄。|
|[CMetaFileDC:關閉增強](#closeenhanced)|關閉增強元檔設備上下文並創建增強元檔句柄。|
|[CMetaFileDC:建立](#create)|創建 Windows 檔裝置上下文並將其附加`CMetaFileDC`到 物件。|
|[CMetaFileDC:建立增強](#createenhanced)|為增強格式的元檔創建元檔設備上下文。|

## <a name="remarks"></a>備註

要實現 Windows 元檔,`CMetaFileDC`請先 創建一個物件。 調用`CMetaFileDC`建構函數,然後調用[Create](#create)成員函數,該函數創建 Windows 元檔設備上下`CMetaFileDC`文並將其附加到 物件。

接下來,將`CMetaFileDC`物件發送您打算重播的CDC GDI 命令的順序。 只能使用建立輸出的 GDI`MoveTo`指令`LineTo`, 如與 。

將所需命令發送到元檔後,調用`Close`成員函數,該函數將關閉元檔設備上下文並返回元檔句柄。 然後釋放物件`CMetaFileDC`。

[然後,CDC::PlayMetaFile](../../mfc/reference/cdc-class.md#playmetafile)可以使用元檔句柄反覆播放元檔。 元檔也可以由 Windows 函數(如[CopyMetaFile)](/windows/win32/api/wingdi/nf-wingdi-copymetafilew)進行操作,這些函數將中檔案複製到磁碟。

當不再需要元檔時,使用[DeleteMetaFile](/windows/win32/api/wingdi/nf-wingdi-deletemetafile) Windows 功能將其從記憶體中刪除。

您還可以實現該`CMetaFileDC`物件,以便它可以同時處理輸出調用和屬性 GDI 調`GetTextExtent`用(如 )。 這種元檔更靈活,可以更輕鬆地重用常規 GDI 代碼,該代碼通常由輸出和屬性調用的組合組成。 類別`CMetaFileDC`繼承兩個裝置中,`m_hDC`並從`m_hAttribDC`CDC 繼承與 。 設備上下文處理所有[CDC](../../mfc/reference/cdc-class.md) GDI`m_hAttribDC`輸出呼叫 ,設備上下文處理所有 CDC `m_hDC` GDI 屬性呼叫。 通常,這兩個設備上下文引用同一設備。 在的情況下`CMetaFileDC`,預設情況下,屬性 DC 設定為 NULL。

創建指向螢幕、印表機或元檔以外的設備的第二個設備上下文,然後調`SetAttribDC`用 成員函數將新設備上下`m_hAttribDC`文與關聯。 GDI 要求的資訊現在將定到`m_hAttribDC`新的 。 輸出 GDI 呼`m_hDC`叫將轉到 ,這表示元檔。

有關 的詳細`CMetaFileDC`資訊 ,請參閱[裝置上下文](../../mfc/device-contexts.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CMetaFileDC`

## <a name="requirements"></a>需求

**標題:** afxext.h

## <a name="cmetafiledcclose"></a><a name="close"></a>CMetaFileDC:關閉

關閉中檔案裝置上下文並建立一個 Windows 檔片檔,該句柄可用於使用[CDC::PlayMetaFile](../../mfc/reference/cdc-class.md#playmetafile)成員函數播放元檔。

```
HMETAFILE Close();
```

### <a name="return-value"></a>傳回值

如果函數成功,則為有效的 HMETAFILE;否則 NULL。

### <a name="remarks"></a>備註

Windows 中繼檔句柄還可用於使用 Windows 函數(如[CopyMetaFile)](/windows/win32/api/wingdi/nf-wingdi-copymetafilew)操作元檔。

使用後透過調用 Windows [DeleteMetaFile](/windows/win32/api/wingdi/nf-wingdi-deletemetafile)功能刪除元檔。

## <a name="cmetafiledccloseenhanced"></a><a name="closeenhanced"></a>CMetaFileDC:關閉增強

關閉增強元文件設備上下文並返回標識增強格式元檔的句柄。

```
HENHMETAFILE CloseEnhanced();
```

### <a name="return-value"></a>傳回值

增強元檔的句柄(如果成功);否則 NULL。

### <a name="remarks"></a>備註

應用程式可以使用此函數傳回的擴增中檔案片控以下工作:

- 顯示儲存在增強中繼的圖片

- 建立增強的中繼檔的複本

- 列舉、編輯或複製增強的中繼檔的單一個紀錄

- 從增強中繼檔案標題檢索元檔案內容的可選說明

- 檢索增強中繼標頭的複本

- 檢索增強的元檔的二進制副本

- 列舉選擇的顏色

- 將增強格式的中繼檔轉換為 Windows 格式的中繼檔

當應用程式不再需要增強的元檔句柄時,它應該通過調用 Win32`DeleteEnhMetaFile`函數來釋放句柄。

## <a name="cmetafiledccmetafiledc"></a><a name="cmetafiledc"></a>CMetaFileDC:CMetaFileDC

分兩`CMetaFileDC`步構造物件。

```
CMetaFileDC();
```

### <a name="remarks"></a>備註

首先,調用`CMetaFileDC`,`Create`然後調用 ,這將創建 Windows 元檔設備上下文`CMetaFileDC`並將其附加到 物件。

## <a name="cmetafiledccreate"></a><a name="create"></a>CMetaFileDC:建立

分兩`CMetaFileDC`步構造物件。

```
BOOL Create(LPCTSTR lpszFilename = NULL);
```

### <a name="parameters"></a>參數

*lpszFile 名稱*<br/>
指向 null 終止的字串。 指定要建立的元檔的檔名。 如果*lpszFile 名*為 NULL,則建立新的記憶體中元檔。

### <a name="return-value"></a>傳回值

如果函式成功則為非零，否則為 0。

### <a name="remarks"></a>備註

首先調用建構函數`CMetaFileDC`,然後調`Create`用 ,這將創建 Windows 元檔設備上下文`CMetaFileDC`並將其附加到 物件。

## <a name="cmetafiledccreateenhanced"></a><a name="createenhanced"></a>CMetaFileDC:建立增強

為增強格式的元文件創建設備上下文。

```
BOOL CreateEnhanced(
    CDC* pDCRef,
    LPCTSTR lpszFileName,
    LPCRECT lpBounds,
    LPCTSTR lpszDescription);
```

### <a name="parameters"></a>參數

*pDCRef*<br/>
標識增強的元文件的參考設備。

*lpszFile 名稱*<br/>
指向 null 終止的字串。 指定要創建的擴增元檔的檔名。 如果此參數為 NULL,則增強的元檔基於記憶體,當物件被銷毀或調用 Win32`DeleteEnhMetaFile`函數時,其內容將丟失。

*lpBounds*<br/>
指向[RECT](/windows/win32/api/windef/ns-windef-rect)資料結構或[CRect](../../atl-mfc-shared/reference/crect-class.md)物件,該物件以 HIMETRIC 單位(以 .01 毫米的增量)指定要存儲在增強的元檔中的圖片的尺寸。

*lpsz描述*<br/>
指向一個零端接字串,該字串指定創建圖片的應用程式的名稱以及圖片的標題。

### <a name="return-value"></a>傳回值

增強元檔的設備上下文的句柄(如果成功);否則 NULL。

### <a name="remarks"></a>備註

此DC可用於存儲與設備無關的圖片。

Windows 使用*pDCRef*參數識別的參考設備來記錄最初顯示圖片的設備的解析度和單位。 如果*pDCRef*參數為 NULL,則使用當前顯示設備進行參考。

`RECT` *lpBounds*參數指向的數據結構的左側和頂部成員必須分別小於右側和底部成員。 沿矩形邊緣的點包含在圖片中。 如果*lpBounds*為 NULL,則圖形裝置介面 (GDI) 計算最小矩形的尺寸,該矩形可以包含應用程式繪製的圖片。 應盡可能提供*lpBounds*參數。

*lpsz描述*參數指向的字串必須在應用程式名稱和圖片名稱之間包含一個空字元,並且必須用兩個空字元終止-例如,"XYZ 圖形編輯器\0Bald Eagle_0_0",其中 |0 表示空字元。 如果*lpsz 描述*為 NULL,則增強元檔標頭中沒有相應的條目。

應用程式使用此函數創建的 DC 將圖形圖片存儲在增強的元檔中。 標識此 DC 的句柄可以傳遞給任何 GDI 函數。

應用程式將圖片存儲在增強的元檔中后,可以通過調用函數在`CDC::PlayMetaFile`任何 輸出設備上顯示圖片。 顯示圖片時,Windows 使用*lpBounds*參數指向的矩形和參考設備的解析度數據來定位和縮放圖片。 此函數傳回的裝置上下文包含與任何新 DC 關聯的相同預設屬性。

應用程式必須使用 Win32`GetWinMetaFileBits`函數將增強的元檔轉換為較舊的 Windows 元檔格式。

增強的中繼檔的檔案名稱應使用 。EMF 擴展。

## <a name="see-also"></a>另請參閱

[CDC 類別](../../mfc/reference/cdc-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
