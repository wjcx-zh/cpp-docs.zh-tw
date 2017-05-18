---
title: "CSocketFile 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSocketFile
- AFXSOCK/CSocketFile
- AFXSOCK/CSocketFile::CSocketFile
dev_langs:
- C++
helpviewer_keywords:
- networks [C++], archive
- serialization [C++], network
- networks [C++], serializing to
- CSocketFile class
- archives [C++], network
- SOCKET handle
ms.assetid: 7924c098-5f72-40d6-989d-42800a47958f
caps.latest.revision: 24
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 6ca331c07e0a9fc48f152042fcccd5c38e743ccf
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="csocketfile-class"></a>CSocketFile 類別
`CFile` 物件，用於透過 Windows Sockets 在網路上傳送和接收資料。  
  
## <a name="syntax"></a>語法  
  
```  
class CSocketFile : public CFile  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CSocketFile::CSocketFile](#csocketfile)|建構 `CSocketFile` 物件。|  
  
## <a name="remarks"></a>備註  
 您可以將附加`CSocketFile`物件傳遞給`CSocket`此用途的物件。 您也可以，而且通常會執行動作，連接`CSocketFile`物件傳遞給`CArchive`簡化傳送及接收資料使用 MFC 序列化的物件。  
  
 若要序列化 （傳送） 資料，您將它插入封存，它會呼叫`CSocketFile`成員函式來將資料寫入`CSocket`物件。 若要還原序列化 （接收） 的資料，您從封存中解壓縮。 這會導致呼叫封存`CSocketFile`從中讀取資料的成員函式`CSocket`物件。  
  
> [!TIP]
>  除了使用`CSocketFile`如這裡所述，您可以使用它做為獨立的檔案物件一樣，您可以使用`CFile`、 其基底類別。 您也可以使用`CSocketFile`與任何封存架構的 MFC 序列化函式。 因為`CSocketFile`不支援的所有`CFile`的功能，某些預設 MFC 序列化函式與不相容`CSocketFile`。 尤其是`CEditView`類別。 您不應該嘗試序列化`CEditView`資料透過`CArchive`物件附加至`CSocketFile`物件使用`CEditView::SerializeRaw`; 使用**CEditView::Serialize**改。 `SerializeRaw`函式必須要有函式，例如 「 檔案 」 物件`Seek`，`CSocketFile`並沒有。  
  
 當您使用`CArchive`與`CSocketFile`和`CSocket`，您可能會發生的情況其中**CSocket::Receive**進入迴圈 (由**PumpMessages(FD_READ)**) 等待要求的位元組數量。 這是因為 Windows 通訊端可以只有一個接收呼叫每個 FD_READ 通知，但`CSocketFile`和`CSocket`允許每個 FD_READ 的多個接收呼叫。 如果您收到 FD_READ 可讀取的資料時，應用程式停止回應。 如果您永遠不會收到另一個 FD_READ，應用程式停止通訊端進行通訊。  
  
 您可以解決這個問題，如下所示。 在`OnReceive`您通訊端類別方法，呼叫**CAsyncSocket::IOCtl (FIONREAD，...)**之前先呼叫`Serialize`訊息類別時從通訊端讀取預期的資料超過一個 TCP 封包 （最大傳輸單位網路中通常至少 1096 個位元組） 的大小的方法。 如果少於所需的可用的資料大小，等待接收，然後才開始讀取的作業的所有資料。  
  
 在下列範例中，`m_dwExpected`是近似的使用者希望接收的位元組數目。 假設您宣告它在其他地方在程式碼中。  
  
 [!code-cpp[NVC_MFCSocketThread #&4;](../../mfc/reference/codesnippet/cpp/csocketfile-class_1.cpp)]  
  
 如需詳細資訊，請參閱[MFC 中的 Windows Sockets](../../mfc/windows-sockets-in-mfc.md)， [Windows Sockets︰ 使用通訊端與封存](../../mfc/windows-sockets-using-sockets-with-archives.md)，以及[Windows Sockets 2 API](http://msdn.microsoft.com/library/windows/desktop/ms740673)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 `CSocketFile`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxsock.h  
  
##  <a name="csocketfile"></a>CSocketFile::CSocketFile  
 建構 `CSocketFile` 物件。  
  
```  
explicit CSocketFile(
    CSocket* pSocket,  
    BOOL bArchiveCompatible = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `pSocket`  
 要附加至的通訊端`CSocketFile`物件。  
  
 `bArchiveCompatible`  
 指定檔案的物件是否用於`CArchive`物件。 傳遞**FALSE**只有當您想要使用`CSocketFile`物件在獨立的方式，就獨立`CFile`物件，但有某些限制。 這個旗標變更如何`CArchive`物件附加至`CSocketFile`物件會管理其進行讀取的緩衝區。  
  
### <a name="remarks"></a>備註  
 物件的解構函式本身解除與關聯通訊端物件當物件超出範圍或被刪除。  
  
> [!NOTE]
>  A`CSocketFile`也可用來當做 （有限制） 的檔案，而不`CArchive`物件。 根據預設，`CSocketFile`建構函式的`bArchiveCompatible`參數是**TRUE**。 這會指定 「 檔案 」 物件是用於封存。 若要使用 「 檔案 」 物件沒有封存，傳遞**FALSE**中`bArchiveCompatible`參數。  
  
 在 「 封存相容 」 模式下，`CSocketFile`物件提供更佳的效能並減少的 < 死結 >。 傳送和接收通訊端等候彼此，或針對常見的資源時，就會發生死結。 可能會發生這種情況下，如果`CArchive`物件從事`CSocketFile`一樣使用`CFile`物件。 使用`CFile`，封存可以假設如果收到比要求的位元組較少，具有已到達檔案結尾。  
  
 使用`CSocketFile`，不過，資料為基礎的訊息緩衝區中可以包含多個訊息，因此接收少於所要求的位元組數目，並不代表檔案結尾。 應用程式不會封鎖在此情況下可能與`CFile`，而且可以繼續從緩衝區讀取訊息，直到緩衝區是空的。 [CArchive::IsBufferEmpty](../../mfc/reference/carchive-class.md#isbufferempty)函式可用於監視封存的緩衝區，在此情況下的狀態。  
  
 如需有關使用`CSocketFile`，請參閱文章[Windows Sockets︰ 使用通訊端與封存](../../mfc/windows-sockets-using-sockets-with-archives.md)和[Windows Sockets︰ 通訊端使用封存的範例](../../mfc/windows-sockets-example-of-sockets-using-archives.md)。  
  
## <a name="see-also"></a>另請參閱  
 [CFile 類別](../../mfc/reference/cfile-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CAsyncSocket 類別](../../mfc/reference/casyncsocket-class.md)   
 [CSocket 類別](../../mfc/reference/csocket-class.md)

