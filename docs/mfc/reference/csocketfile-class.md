---
title: CSocketFile 類別
ms.date: 11/04/2016
f1_keywords:
- CSocketFile
- AFXSOCK/CSocketFile
- AFXSOCK/CSocketFile::CSocketFile
helpviewer_keywords:
- CSocketFile [MFC], CSocketFile
ms.assetid: 7924c098-5f72-40d6-989d-42800a47958f
ms.openlocfilehash: 83810a05925e5c8302240b61d95c131fdd78b426
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318165"
---
# <a name="csocketfile-class"></a>CSocketFile 類別

`CFile` 物件，用於透過 Windows Sockets 在網路上傳送和接收資料。

## <a name="syntax"></a>語法

```
class CSocketFile : public CFile
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[Socket 檔::socket 檔案](#csocketfile)|建構 `CSocketFile` 物件。|

## <a name="remarks"></a>備註

為此,`CSocketFile`可以將物件附加`CSocket`到 物件。 您還可以(通常也可以)將`CSocketFile`物件附加到物件,`CArchive`以簡化使用 MFC 序列化發送和接收數據。

要序列化(發送)數據,請將其插入到存檔中,存檔調用`CSocketFile`成員函數將數據寫`CSocket`入 物件。 要從存檔中提取(接收)數據。 這將導致存檔調用`CSocketFile`成員函數`CSocket`從 物件讀取數據。

> [!TIP]
> 除了按照`CSocketFile`此處所述使用外,還可以將其用作獨立文件物件,就像可以`CFile`使用 它的基類一樣。 您還可以使用`CSocketFile`任何基於存檔的 MFC 序列化功能。 由於`CSocketFile`不支援`CFile`所有功能,因此某些預設 MFC 序列`CSocketFile`化功能與 不相容。 `CEditView`類尤其如此。 不應嘗試`CEditView``CArchive``CSocketFile``CEditView::SerializeRaw`使用改`CEditView::Serialize`用。 函數`SerializeRaw`期望檔案物件有沒有`Seek``CSocketFile`的函數,例如 。

使用`CArchive``CSocketFile``CSocket`和 時,`CSocket::Receive`可能會遇到 輸入`PumpMessages(FD_READ)`迴圈 (由 ) 等待請求的位元組數的情況。 這是因為 Windows 套接字僅允許每個FD_READ通知一個`CSocketFile``CSocket`recv 調用,並且允許每個FD_READ多個 recv 調用。 如果在沒有要讀取的數據時獲得FD_READ,應用程式將掛起。 如果您從未獲得另一個FD_READ,應用程式將停止通過套接字進行通信。

您可以按照如下方式解決此問題。 在`OnReceive`套接字類中,當`CAsyncSocket::IOCtl(FIONREAD, ...)`從套接字讀`Serialize`取的預期數據超過一個 TCP 數據包(網路介質的最大傳輸單元,通常至少 1096 位元組)時,在調用消息類的方法之前調用。 如果可用數據的大小小於所需大小,請等待接收所有數據,然後僅啟動讀取操作。

在下面的範例中,`m_dwExpected`是使用者希望接收的大約位元組數。 假定您在代碼的其他位置聲明它。

[!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocketfile-class_1.cpp)]

有關詳細資訊,請參閱 MFC 中的[Windows 套接字](../../mfc/windows-sockets-in-mfc.md)[、Windows 通訊卡字:使用帶存檔的套接字](../../mfc/windows-sockets-using-sockets-with-archives.md)以及[Windows 通訊通訊的](/windows/win32/WinSock/windows-sockets-start-page-2)位址 。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`CSocketFile`

## <a name="requirements"></a>需求

**標題:** afxsock.h

## <a name="csocketfilecsocketfile"></a><a name="csocketfile"></a>Socket 檔::socket 檔案

建構 `CSocketFile` 物件。

```
explicit CSocketFile(
    CSocket* pSocket,
    BOOL bArchiveCompatible = TRUE);
```

### <a name="parameters"></a>參數

*pSocket*<br/>
要附加到`CSocketFile`物件的套接字。

*b 存檔相容*<br/>
指定檔物件是否用於`CArchive`物件。 僅當您希望以獨立方式使用`CSocketFile`物件時,才像`CFile`獨立 物件一樣,具有某些限制,才傳遞 FALSE。 此標誌更改附加到`CArchive``CSocketFile`物件的物件管理其緩衝區以進行讀取的方式。

### <a name="remarks"></a>備註

當物件超出範圍或刪除時,物件的析構函數會與套接字物件分離。

> [!NOTE]
> 還可以`CSocketFile`用作沒有`CArchive`物件的(受限)檔。 預設情況下,`CSocketFile`建構函數的*bArchive 相容*參數為 TRUE。 這指定檔案物件用於存檔。 要使用沒有存檔的檔案物件,請使用*bArchive 相容*參數中的 FALSE。

在其「存檔相容」模式下,`CSocketFile`物件提供更好的性能並減少「死鎖」的危險。 當發送和接收套接字相互等待或等待公共資源時,將發生死鎖。 如果`CArchive`物件的工作方式`CSocketFile``CFile`與 物件一起工作,則可能發生此情況。 使用`CFile`時,存檔可以假定,如果接收的位元組數少於其請求的位元組數,則已達到檔結尾。

但是`CSocketFile`,對於 ,數據是基於消息的;緩衝區可以包含多條消息,因此接收少於請求的位元組數並不意味著檔結束。 在這種情況下,應用程式不會像`CFile`在中阻止,因為它可以使用 ,它可以繼續從緩衝區讀取消息,直到緩衝區為空。 [在這種情況下,CArchive:isBufferEmpty](../../mfc/reference/carchive-class.md#isbufferempty)函數可用於監視存檔緩衝區的狀態。

有關`CSocketFile`使用的詳細資訊,請參閱[Windows 通訊卡字:使用帶存檔](../../mfc/windows-sockets-using-sockets-with-archives.md)與 Windows[通訊的 socket:使用存檔的 socket 範例](../../mfc/windows-sockets-example-of-sockets-using-archives.md)。

## <a name="see-also"></a>另請參閱

[CFile 類別](../../mfc/reference/cfile-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CAsyncSocket 類別](../../mfc/reference/casyncsocket-class.md)<br/>
[CSocket 類別](../../mfc/reference/csocket-class.md)
