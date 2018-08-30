---
title: CSocketFile 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSocketFile
- AFXSOCK/CSocketFile
- AFXSOCK/CSocketFile::CSocketFile
dev_langs:
- C++
helpviewer_keywords:
- CSocketFile [MFC], CSocketFile
ms.assetid: 7924c098-5f72-40d6-989d-42800a47958f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c4c74d1ab89c45b7871cf0b4fa0d8a6350bc1425
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43209633"
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
|[CSocketFile::CSocketFile](#csocketfile)|建構 `CSocketFile` 物件。|  
  
## <a name="remarks"></a>備註  
 您可以將附加`CSocketFile`物件至`CSocket`針對此用途的物件。 您也可以，而且通常會執行，連接`CSocketFile`物件至`CArchive`簡化傳送和接收資料使用 MFC 序列化的物件。  
  
 若要序列化 （傳送） 資料，您將它插入封存，它會呼叫`CSocketFile`成員函式，將資料寫入至`CSocket`物件。 若要還原序列化 （接收） 從封存解壓縮資料。 這會導致呼叫封存`CSocketFile`成員函式來讀取資料，從`CSocket`物件。  
  
> [!TIP]
>  除了使用`CSocketFile`如下所述，您可以使用它定義為獨立檔案的物件，如同您對`CFile`、 其基底類別。 您也可以使用`CSocketFile`與任何封存型 MFC 序列化函式。 因為`CSocketFile`不支援的所有`CFile`的功能，有些預設 MFC 序列化函式與不相容`CSocketFile`。 特別的是`CEditView`類別。 您不應該嘗試序列化`CEditView`透過資料`CArchive`物件附加至`CSocketFile`物件使用`CEditView::SerializeRaw`; 使用`CEditView::Serialize`改。 `SerializeRaw`函式必須要有函式，例如 「 檔案 」 物件`Seek`，、 該`CSocketFile`並沒有。  
  
 當您使用`CArchive`與`CSocketFile`並`CSocket`，您可能會遇到一種情況其中`CSocket::Receive`進入迴圈 (由`PumpMessages(FD_READ)`) 等待所要求的位元組數量。 這是因為 Windows 通訊端允許 FD_READ 通知，每一個接收呼叫，但`CSocketFile`和`CSocket`允許每 FD_READ 的多個接收呼叫。 如果可讀取的資料時，您會收到 FD_READ，應用程式會停止回應。 如果您從未收到另一個 FD_READ，應用程式會停止透過通訊端進行通訊。  
  
 您可以解決這個問題，如下所示。 在 `OnReceive`通訊端類別，呼叫方法`CAsyncSocket::IOCtl(FIONREAD, ...)`之前先呼叫`Serialize`訊息類別時從通訊端讀取預期的資料超過一個 TCP 封包的網路中 （最大傳輸單位的大小方法通常至少 1096 位元組為單位)。 如果少於所需的可用資料的大小，等待要接收，然後才開始讀取的作業的所有資料。  
  
 在下列範例中，`m_dwExpected`是近似的使用者預期收到的位元組數目。 它會假設，您將它宣告其他位置中您的程式碼。  
  
 [!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocketfile-class_1.cpp)]  
  
 如需詳細資訊，請參閱 < [MFC 中的 Windows Sockets](../../mfc/windows-sockets-in-mfc.md)， [Windows Sockets： 使用通訊端與封存](../../mfc/windows-sockets-using-sockets-with-archives.md)，以及[Windows Sockets 2 API](/windows/desktop/WinSock/windows-sockets-start-page-2)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 `CSocketFile`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxsock.h  
  
##  <a name="csocketfile"></a>  CSocketFile::CSocketFile  
 建構 `CSocketFile` 物件。  
  
```  
explicit CSocketFile(
    CSocket* pSocket,  
    BOOL bArchiveCompatible = TRUE);
```  
  
### <a name="parameters"></a>參數  
 *pSocket*  
 若要將附加到通訊端`CSocketFile`物件。  
  
 *bArchiveCompatible*  
 指定檔案的物件是否用於`CArchive`物件。 傳遞 FALSE，只有當您想要使用時，才`CSocketFile`物件中獨立的方式，如同獨立`CFile`物件，但有某些限制。 這個旗標變更如何`CArchive`物件附加至`CSocketFile`物件會管理其進行讀取的緩衝區。  
  
### <a name="remarks"></a>備註  
 物件的解構函式本身解除與關聯的通訊端物件當物件超出範圍，或刪除。  
  
> [!NOTE]
>  A`CSocketFile`也可用來當做 （有限制） 的檔案，而不`CArchive`物件。 根據預設，`CSocketFile`建構函式*bArchiveCompatible*參數為 TRUE。 這會指定 「 檔案 」 物件是用於封存。 若要使用 「 檔案 」 物件但未封存，傳遞 FALSE *bArchiveCompatible*參數。  
  
 在 「 封存相容 」 模式下，`CSocketFile`物件提供更佳的效能，並減少產生風險的 < 死結 >。 傳送和接收通訊端等候彼此，或針對常見的資源時，就會發生死結。 如果發生這種情況，可能`CArchive`物件所從事`CSocketFile`一樣的方式`CFile`物件。 使用`CFile`，封存會假設它收到較少的位元組，比要求時，如果有已到達檔案結尾。  
  
 使用`CSocketFile`，不過，資料為基礎的訊息緩衝區中可以包含多個訊息，因此接收少於所要求的位元組數目，並不表示檔案結尾。 應用程式不會封鎖在此情況下，它可能與`CFile`，因此能夠繼續從緩衝區讀取訊息，直到緩衝區是空的。 [CArchive::IsBufferEmpty](../../mfc/reference/carchive-class.md#isbufferempty)函式可用於監視的狀態這種情況的封存的緩衝區。  
  
 如需有關使用`CSocketFile`，請參閱文章[Windows Sockets： 使用通訊端與封存](../../mfc/windows-sockets-using-sockets-with-archives.md)和[Windows Sockets： 通訊端使用封存的範例](../../mfc/windows-sockets-example-of-sockets-using-archives.md)。  
  
## <a name="see-also"></a>另請參閱  
 [CFile 類別](../../mfc/reference/cfile-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CAsyncSocket 類別](../../mfc/reference/casyncsocket-class.md)   
 [CSocket 類別](../../mfc/reference/csocket-class.md)
