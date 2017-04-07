---
title: "CMemFile 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMemFile
- AFX/CMemFile
- AFX/CMemFile::CMemFile
- AFX/CMemFile::Attach
- AFX/CMemFile::Detach
- AFX/CMemFile::Alloc
- AFX/CMemFile::Free
- AFX/CMemFile::GrowFile
- AFX/CMemFile::Memcpy
- AFX/CMemFile::Realloc
dev_langs:
- C++
helpviewer_keywords:
- memory files
- CMemFile class
- temporary files, memory files
ms.assetid: 20e86515-e465-4f73-b2ea-e49789d63165
caps.latest.revision: 21
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 9851e050b05ac129e5e498c7ea99dfedddc79e54
ms.lasthandoff: 02/24/2017

---
# <a name="cmemfile-class"></a>CMemFile 類別
[CFile](../../mfc/reference/cfile-class.md)-衍生類別，可支援記憶體檔案。  
  
## <a name="syntax"></a>語法  
  
```  
class CMemFile : public CFile  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMemFile::CMemFile](#cmemfile)|建構記憶體檔案物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMemFile::Attach](#attach)|將附加的記憶體區塊`CMemFile`。|  
|[CMemFile::Detach](#detach)|中斷連結中的記憶體區塊`CMemFile`和卸離的記憶體區塊中傳回的指標。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMemFile::Alloc](#alloc)|覆寫以修改記憶體配置行為。|  
|[CMemFile::Free](#free)|覆寫以修改記憶體解除配置行為。|  
|[CMemFile::GrowFile](#growfile)|覆寫檔案時，修改行為。|  
|[CMemFile::Memcpy](#memcpy)|覆寫以修改讀取和寫入檔案時，記憶體複製行為。|  
|[CMemFile::Realloc](#realloc)|覆寫以修改記憶體配置行為。|  
  
## <a name="remarks"></a>備註  
 這些記憶體檔案的行為如同磁碟檔案不同之處在於檔案會儲存在 RAM 中，而不是在磁碟上。 記憶體檔案有助於快速暫時存放或傳輸未經處理位元組或序列化的物件之間獨立的處理序。  
  
 `CMemFile`物件，可以自動配置它們自己的記憶體，或您可以將附加至您自己的記憶體區塊`CMemFile`物件呼叫[附加](#attach)。 在任一情況下，自動成長的記憶體檔案的記憶體配置在`nGrowBytes`-如果大小遞增`nGrowBytes`不是零。  
  
 記憶體區塊會自動刪除時的解構`CMemFile`物件記憶體的最初配置的`CMemFile`物件; 否則您必須負責解除配置您附加至物件的記憶體。  
  
 您可以透過提供當您從中斷連結的指標存取的記憶體區塊`CMemFile`物件呼叫[卸離](#detach)。  
  
 最常見的使用`CMemFile`是建立`CMemFile`物件，並使用藉由呼叫[CFile](../../mfc/reference/cfile-class.md)成員函式。 請注意，建立`CMemFile`會自動開啟它︰ 您不呼叫[CFile::Open](../../mfc/reference/cfile-class.md#open)，只用於磁碟檔案。 因為`CMemFile`不會使用磁碟檔案，資料成員`CFile::m_hFile`未使用。  
  
 `CFile`成員函式[重複](../../mfc/reference/cfile-class.md#duplicate)， [LockRange](../../mfc/reference/cfile-class.md#lockrange)，和[UnlockRange](../../mfc/reference/cfile-class.md#unlockrange)並未實作`CMemFile`。 如果您呼叫這些函式上`CMemFile`物件時，就會[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。  
  
 `CMemFile`使用執行階段程式庫函式[malloc](../../c-runtime-library/reference/malloc.md)， [realloc](../../c-runtime-library/reference/realloc.md)，和[免費](../../c-runtime-library/reference/free.md)配置、 重新配置和解除配置記憶體，以及內建函式[memcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md)區塊複製記憶體讀取和寫入時。 如果您想要變更此行為時`CMemFile`成長檔案中，衍生您自己從`CMemFile`並覆寫適當的函式。  
  
 如需有關`CMemFile`，請參閱文章[MFC 中的檔案](../../mfc/files-in-mfc.md)和[記憶體管理 (MFC)](../../mfc/memory-management.md)看[檔案處理](../../c-runtime-library/file-handling.md)中*執行階段程式庫參考*。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 `CMemFile`  
  
## <a name="requirements"></a>需求  
 **標頭：** afx.h  
  
##  <a name="alloc"></a>CMemFile::Alloc  
 此函式會呼叫`CMemFile`成員函式。  
  
```  
virtual BYTE* Alloc(SIZE_T nBytes);
```  
  
### <a name="parameters"></a>參數  
 `nBytes`  
 記憶體配置的位元組數。  
  
### <a name="return-value"></a>傳回值  
 已配置的記憶體區塊的指標或**NULL**若配置失敗。  
  
### <a name="remarks"></a>備註  
 覆寫這個函式來實作自訂的記憶體配置。 如果您覆寫這個函式，您可能需要覆寫[免費](#free)和[Realloc](#realloc)以及。  
  
 預設實作會使用執行階段程式庫函式[malloc](../../c-runtime-library/reference/malloc.md)配置記憶體。  
  
##  <a name="attach"></a>CMemFile::Attach  
 呼叫此函式可附加的記憶體區塊`CMemFile`。  
  
```  
void Attach(
    BYTE* lpBuffer,  
    UINT nBufferSize,  
    UINT nGrowBytes = 0);
```  
  
### <a name="parameters"></a>參數  
 `lpBuffer`  
 要附加至緩衝區的指標`CMemFile`。  
  
 `nBufferSize`  
 整數，指定緩衝區的大小 （位元組）。  
  
 `nGrowBytes`  
 以位元組為單位的記憶體配置遞增值。  
  
### <a name="remarks"></a>備註  
 這會導致`CMemFile`作為記憶體檔案中的記憶體區塊。  
  
 如果`nGrowBytes`為 0，`CMemFile`將設定檔案長度為`nBufferSize`。 這表示，記憶體區塊中的資料之前已附加到`CMemFile`做檔案。 以這種方式建立記憶體檔案無法成長。  
  
 由於檔案無法增長，小心不要將導致`CMemFile`檔案成長的嘗試。 例如，不要呼叫`CMemFile`的覆寫[CFile:Write](../../mfc/reference/cfile-class.md#write)來寫入超過結尾或不要呼叫[CFile:SetLength](../../mfc/reference/cfile-class.md#setlength)長度超過`nBufferSize`。  
  
 如果`nGrowBytes`大於 0，`CMemFile`會略過連結之後的記憶體區塊的內容。 您必須撰寫記憶體檔案的內容，從可用的使用`CMemFile`覆寫`CFile::Write`。 如果您嘗試寫入超過檔案結尾，或檔案成長藉由呼叫`CMemFile`覆寫`CFile::SetLength`，`CMemFile`會成長量的記憶體配置`nGrowBytes`。 如果您傳遞給記憶體區塊成長的記憶體配置將會失敗**附加**不相容的方法以配置[配置](#alloc)。 預設實作與`Alloc`，您必須配置的記憶體以執行階段程式庫函數[malloc](../../c-runtime-library/reference/malloc.md)或[calloc](../../c-runtime-library/reference/calloc.md)。  
  
##  <a name="cmemfile"></a>CMemFile::CMemFile  
 第一個多載會開啟空白記憶體檔案。  
  
```  
CMemFile(UINT nGrowBytes = 1024);

 
CMemFile(
    BYTE* lpBuffer,  
    UINT nBufferSize,  
    UINT nGrowBytes = 0);
```  
  
### <a name="parameters"></a>參數  
 `nGrowBytes`  
 以位元組為單位的記憶體配置遞增值。  
  
 *lpBuffe*r  
 接收資訊大小的緩衝區指標`nBufferSize`。  
  
 `nBufferSize`  
 整數，指定檔案緩衝區的大小 （位元組）。  
  
### <a name="remarks"></a>備註  
 請注意，建構函式開啟的檔案，您不應該呼叫[CFile::Open](../../mfc/reference/cfile-class.md#open)。  
  
 第二個多載作用相同，因為如果您使用第一個建構函式，並立即呼叫[附加](#attach)使用相同的參數。 請參閱**附加**如需詳細資訊。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCFiles #&36;](../../atl-mfc-shared/reference/codesnippet/cpp/cmemfile-class_1.cpp)]  
  
##  <a name="detach"></a>CMemFile::Detach  
 呼叫此函式可取得正在使用的記憶體區塊的指標`CMemFile`。  
  
```  
BYTE* Detach();
```  
  
### <a name="return-value"></a>傳回值  
 包含記憶體檔案的內容的記憶體區塊指標。  
  
### <a name="remarks"></a>備註  
 呼叫此函式也會關閉`CMemFile`。 您可以重新連接到的記憶體區塊`CMemFile`藉由呼叫[附加](#attach)。 如果您想要附加檔案，並在其中使用的資料，您應該呼叫[CFile::GetLength](../../mfc/reference/cfile-class.md#getlength)取得的檔案，然後再呼叫長度**卸離**。 請注意，如果您附加至的記憶體區塊`CMemFile`好讓您可以使用它的資料 ( `nGrowBytes` = = 0)，則您將無法檔案成長的記憶體。  
  
##  <a name="free"></a>CMemFile::Free  
 此函式會呼叫`CMemFile`成員函式。  
  
```  
virtual void Free(BYTE* lpMem);
```  
  
### <a name="parameters"></a>參數  
 `lpMem`  
 解除配置的記憶體指標*。*  
  
### <a name="remarks"></a>備註  
 覆寫這個函式來實作自訂記憶體解除配置。 如果您覆寫這個函式，您可能需要覆寫[配置](#alloc)和[Realloc](#realloc)以及。  
  
##  <a name="growfile"></a>CMemFile::GrowFile  
 會呼叫此函數的數個`CMemFile`成員函式。  
  
```  
virtual void GrowFile(SIZE_T dwNewLen);
```  
  
### <a name="parameters"></a>參數  
 `dwNewLen`  
 新的記憶體檔案的大小。  
  
### <a name="remarks"></a>備註  
 您可以覆寫它如果您想要變更如何`CMemFile`成長的檔案。 預設實作會呼叫[Realloc](#realloc)成長的現有區塊 (或[配置](#alloc)建立記憶體區塊)，配置記憶體的倍數`nGrowBytes`建構函式中指定的值或[附加](#attach)呼叫。  
  
##  <a name="memcpy"></a>CMemFile::Memcpy  
 此函式會呼叫`CMemFile`的覆寫[CFile::Read](../../mfc/reference/cfile-class.md#read)和[CFile::Write](../../mfc/reference/cfile-class.md#write)傳輸資料的記憶體檔案。  
  
```  
virtual BYTE* Memcpy(
    BYTE* lpMemTarget,  
    const BYTE* lpMemSource,  
    SIZE_T nBytes);
```  
  
### <a name="parameters"></a>參數  
 `lpMemTarget`  
 將複製的來源記憶體的記憶體區塊的指標。  
  
 `lpMemSource`  
 來源記憶體區塊指標。  
  
 `nBytes`  
 要複製的位元組數目。  
  
### <a name="return-value"></a>傳回值  
 `lpMemTarget` 的複本。  
  
### <a name="remarks"></a>備註  
 如果您想要變更的方式覆寫此函數，`CMemFile`沒有這些記憶體複本。  
  
##  <a name="realloc"></a>CMemFile::Realloc  
 此函式會呼叫`CMemFile`成員函式。  
  
```  
virtual BYTE* Realloc(
    BYTE* lpMem,  
    SIZE_T nBytes);
```  
  
### <a name="parameters"></a>參數  
 `lpMem`  
 若要重新配置的記憶體區塊指標。  
  
 `nBytes`  
 新的記憶體區塊的大小。  
  
### <a name="return-value"></a>傳回值  
 已重新配置，可能是移動之記憶體區塊的指標或**NULL**重新配置失敗。  
  
### <a name="remarks"></a>備註  
 覆寫這個函式來實作自訂記憶體配置。 如果您覆寫這個函式，您可能需要覆寫[配置](#alloc)和[免費](#free)以及。  
  
## <a name="see-also"></a>另請參閱  
 [CFile 類別](../../mfc/reference/cfile-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)




