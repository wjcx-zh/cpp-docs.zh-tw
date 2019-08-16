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
ms.openlocfilehash: 3b969f81c0c6e1868a66aeaa1c4d9339792062df
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502454"
---
# <a name="csocketfile-class"></a>CSocketFile 類別

`CFile` 物件，用於透過 Windows Sockets 在網路上傳送和接收資料。

## <a name="syntax"></a>語法

```
class CSocketFile : public CFile
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CSocketFile::CSocketFile](#csocketfile)|建構 `CSocketFile` 物件。|

## <a name="remarks"></a>備註

基於此目的, `CSocketFile`您可以將`CSocket`物件附加至物件。 您也可以和通常會將`CSocketFile`物件附加`CArchive`至物件, 以簡化使用 MFC 序列化傳送和接收資料的動作。

若要序列化 (傳送) 資料, 請將它插入封存中, 這`CSocketFile`會呼叫成員函式將資料`CSocket`寫入物件。 若要還原序列化 (接收) 資料, 您可以從封存中解壓縮。 這會導致封存呼叫`CSocketFile`成員函式, 以`CSocket`從物件讀取資料。

> [!TIP]
>  除了如`CSocketFile`這裡所述使用之外, 您還可以使用它做為獨立的檔案物件, 就像您`CFile`在使用它的基類一樣。 您也可以搭配`CSocketFile`任何以保存為基礎的 MFC 序列化函式使用。 由於`CSocketFile`不支援`CFile`所有的功能, 因此某些預設 MFC 序列化函數與`CSocketFile`不相容。 這特別適用于`CEditView`類別。 您不應該嘗試使用`CEditView` `CSocketFile` `CArchive` 附加至物件`CEditView::Serialize`的物件來序列化資料, 請改用。 `CEditView::SerializeRaw` 函式預期檔案物件具有不具有的`CSocketFile`函式, `Seek`例如。 `SerializeRaw`

當您使用`CArchive` `CSocketFile`搭配和`CSocket`時, 您可能會遇到`CSocket::Receive`進入迴圈`PumpMessages(FD_READ)`的情況, 也就是等候要求的位元組數量。 這是因為 Windows 通訊端只允許每個 FD_READ 通知一個接收呼叫`CSocketFile` , `CSocket`但是每個 FD_READ 都允許多個接收呼叫。 如果您在沒有可讀取的資料時收到 FD_READ, 應用程式會停止回應。 如果您從未取得另一個 FD_READ, 應用程式會停止透過通訊端進行通訊。

您可以解決這個問題, 如下所示。 在您`OnReceive`的 socket 類別的方法中, `CAsyncSocket::IOCtl(FIONREAD, ...)`在從通訊端`Serialize`讀取預期的資料超過一個 TCP 封包的大小 (網路媒體的最大傳輸單位) 之前, 呼叫 message 類別的方法。, 通常至少是1096個位元組)。 如果可用資料的大小小於所需, 請等候所有資料都被接收, 然後才啟動讀取作業。

在下列範例中, `m_dwExpected`是使用者預期接收的大約位元組數目。 假設您在程式碼中的其他位置宣告它。

[!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocketfile-class_1.cpp)]

如需詳細資訊, 請參閱[MFC 中的 windows 通訊端](../../mfc/windows-sockets-in-mfc.md)、 [windows socket:搭配使用通訊端](../../mfc/windows-sockets-using-sockets-with-archives.md)與封存, 以及[Windows socket 2 API](/windows/win32/WinSock/windows-sockets-start-page-2)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`CSocketFile`

## <a name="requirements"></a>需求

**標頭:** afxsock。h

##  <a name="csocketfile"></a>CSocketFile:: CSocketFile

建構 `CSocketFile` 物件。

```
explicit CSocketFile(
    CSocket* pSocket,
    BOOL bArchiveCompatible = TRUE);
```

### <a name="parameters"></a>參數

*pSocket*<br/>
要附加至`CSocketFile`物件的通訊端。

*bArchiveCompatible*<br/>
指定檔案物件是否與`CArchive`物件搭配使用。 只有當您想要以獨立方式使用`CSocketFile`物件, 就像是獨立`CFile`物件, 但有某些限制, 才傳遞 FALSE。 這個旗標會變更`CArchive`附加`CSocketFile`至物件的物件如何管理其緩衝區以進行讀取。

### <a name="remarks"></a>備註

當物件超出範圍或遭到刪除時, 物件的析構函式會解除其本身與通訊端物件的比對。

> [!NOTE]
>  也可以用來做為`CArchive`沒有物件的 (受限) 檔案。 `CSocketFile` 根據預設, 此`CSocketFile`函數的*bArchiveCompatible*參數為 TRUE。 這會指定檔案物件用於封存。 若要使用不含封存的 file 物件, 請在*bArchiveCompatible*參數中傳遞 FALSE。

在其「封存相容」模式中, `CSocketFile`物件可提供較佳的效能, 並降低「鎖死」的危險。 當傳送和接收通訊端彼此等待, 或針對通用資源時, 就會發生鎖死。 如果`CArchive`物件`CFile`以物件處理的方式運作, 則可能會發生這種情況。 `CSocketFile` 使用`CFile`時, 封存可以假設如果接收的位元組數比要求的還要少, 就會達到檔案結尾。

不過`CSocketFile`, 資料是以訊息為基礎; 緩衝區可以包含多個訊息, 因此接收的位元組數目少於所要求的位元組數, 並不代表檔案結尾。 應用程式在此情況下不會如其`CFile`所述封鎖, 而且它可以繼續從緩衝區讀取訊息, 直到緩衝區是空的為止。 [CArchive:: IsBufferEmpty](../../mfc/reference/carchive-class.md#isbufferempty)函數適用于在這種情況下監視封存緩衝區的狀態。

如需使用的`CSocketFile`詳細資訊, 請參閱[Windows socket:搭配使用通訊端](../../mfc/windows-sockets-using-sockets-with-archives.md)與[封存和 Windows 通訊端:使用封存的通訊端](../../mfc/windows-sockets-example-of-sockets-using-archives.md)範例。

## <a name="see-also"></a>另請參閱

[CFile 類別](../../mfc/reference/cfile-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CAsyncSocket 類別](../../mfc/reference/casyncsocket-class.md)<br/>
[CSocket 類別](../../mfc/reference/csocket-class.md)
