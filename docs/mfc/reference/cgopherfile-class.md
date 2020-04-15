---
title: CGopherFile 類別
ms.date: 11/04/2016
f1_keywords:
- CGopherFile
- AFXINET/CGopherFile
- AFXINET/CGopherFile::CGopherFile
helpviewer_keywords:
- CGopherFile [MFC], CGopherFile
ms.assetid: 3ca9898f-8cdb-4495-bbde-46d40100feda
ms.openlocfilehash: e157a4509fe30b814a1834690a675906ac82afe7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373698"
---
# <a name="cgopherfile-class"></a>CGopherFile 類別

提供在 Gopher 伺服器上尋找和讀取檔案的功能。

> [!NOTE]
> 類`CGopherConnection``CGopherFile` `CGopherFileFind`、`CGopherLocator`、 及其成員已被棄用,因為它們在 Windows XP 平臺上不工作,但它們將繼續在較早的平臺上工作。

## <a name="syntax"></a>語法

```
class CGopherFile : public CInternetFile
```

## <a name="members"></a>成員

### <a name="protected-constructors"></a>受保護的建構函式

|名稱|描述|
|----------|-----------------|
|[CGopher檔:CGopher檔案](#cgopherfile)|建構 `CGopherFile` 物件。|

## <a name="remarks"></a>備註

gopher 服務不允許使用者將數據寫入 gopher 檔,因為此服務主要用作功能表驅動的用於查找資訊的介面。 成員`CGopherFile`函`Write`數`WriteString`,`Flush`與`CGopherFile`未為實現 。 在`CGopherFile`物件上調用這些函數,傳回[CNot 支援異常](../../mfc/reference/cnotsupportedexception-class.md)。

要瞭解有關如何`CGopherFile`與其他 MFC Internet 類合作,請參閱[WinInet](../../mfc/win32-internet-extensions-wininet.md)的 Internet 程式設計文章。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CStdioFile](../../mfc/reference/cstdiofile-class.md)

[CInternetFile](../../mfc/reference/cinternetfile-class.md)

`CGopherFile`

## <a name="requirements"></a>需求

**標題:** afxinet.h

## <a name="cgopherfilecgopherfile"></a><a name="cgopherfile"></a>CGopher檔:CGopher檔案

呼叫此成員函數以建構物件`CGopherFile`。

```
CGopherFile(
    HINTERNET hFile,
    CGopherLocator& refLocator,
    CGopherConnection* pConnection);

CGopherFile(
    HINTERNET hFile,
    HINTERNET hSession,
    LPCTSTR pstrLocator,
    DWORD dwLocLen,
    DWORD_PTR dwContext);
```

### <a name="parameters"></a>參數

*hFile*<br/>
HINTERNET 檔的句柄。

*參考定位器*<br/>
對[CGopher 定位器物件的參考](../../mfc/reference/cgopherlocator-class.md)。

*pConnection*<br/>
指向[Gopher 連接](../../mfc/reference/cgopherconnection-class.md)物件的指標。

*h 工作階段*<br/>
當前 Internet 作業階段的句柄。

*pstrLocator*<br/>
指向用於定位 gopher 伺服器的字串的指標。 有關 gopher 定位器的詳細資訊,請參閱[Gopher 工作階段](cgopherlocator-class.md)。

*德洛克倫*<br/>
包含*pstrLocator*中的位元組數的 DWORD。

*dwContext*<br/>
指向要打開的檔的上下文標識符的指標。

### <a name="remarks"></a>備註

您需要一個`CGopherFile`物件在 gopher Internet 工作階段期間從檔讀取。

您從不直接創建`CGopherFile`物件。 相反,調用[CGopher 連接::打開檔](../../mfc/reference/cgopherconnection-class.md#openfile)以在 gopher 伺服器上打開檔。

## <a name="see-also"></a>另請參閱

[C 網際網路檔案類別](../../mfc/reference/cinternetfile-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[C 網際網路檔案類別](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherLocator 類別](../../mfc/reference/cgopherlocator-class.md)<br/>
[CGopherFileFind 類別](../../mfc/reference/cgopherfilefind-class.md)<br/>
[CGopherConnection 類別](../../mfc/reference/cgopherconnection-class.md)
