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
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 735f0a5653782f6f42b9dc9ad20e91e94a825f6c
ms.lasthandoff: 04/04/2017

---
# <a name="cmemfile-class"></a>CMemFile 類別
[CFile](../../mfc/reference/cfile-class.md)-衍生的類別支援記憶體檔案。  
  
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
|[CMemFile::Detach](#detach)|中斷連結中的記憶體區塊`CMemFile`和讓指標回到卸離的記憶體區塊。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMemFile::Alloc](#alloc)|若要修改的記憶體配置行為會覆寫。|  
|[CMemFile::Free](#free)|覆寫以修改記憶體解除配置行為。|  
|[CMemFile::GrowFile](#growfile)|覆寫以修改增大檔案時的行為。|  
|[CMemFile::Memcpy](#memcpy)|覆寫以修改讀取和寫入檔案時，記憶體複製行為。|  
|[CMemFile::Realloc](#realloc)|覆寫以修改記憶體重新配置行為。|  
  
## <a name="remarks"></a>備註  
 這些記憶體檔案的行為與磁碟檔案之處在於檔案儲存在 RAM 中，而不是磁碟上。 記憶體檔案有助於快速暫存儲存位置或傳送未經處理位元組或序列化的獨立處理序之間的物件。  
  
 `CMemFile`物件可以自動配置自己的記憶體，或者您可以將附加到您自己的記憶體區塊`CMemFile`藉由呼叫物件[附加](#attach)。 在任一情況下，自動成長的記憶體檔案的記憶體配置中`nGrowBytes`-如果大小為增量單位`nGrowBytes`不是零。  
  
 解構時將會自動刪除記憶體區塊`CMemFile`物件記憶體的原始配置的`CMemFile`物件; 否則您必須負責解除配置您附加至物件的記憶體。  
  
 您可以透過指標提供當您將它從卸離時存取的記憶體區塊`CMemFile`藉由呼叫物件[卸離](#detach)。  
  
 最常見的用法`CMemFile`是建立`CMemFile`物件，並使用藉由呼叫[CFile](../../mfc/reference/cfile-class.md)成員函式。 請注意，建立`CMemFile`會自動開啟它︰ 您不會呼叫[CFile::Open](../../mfc/reference/cfile-class.md#open)，僅用於磁碟檔案。 因為`CMemFile`不會使用磁碟檔案，資料成員`CFile::m_hFile`未使用。  
  
 `CFile`成員函式[重複](../../mfc/reference/cfile-class.md#duplicate)， [LockRange](../../mfc/reference/cfile-class.md#lockrange)，和[UnlockRange](../../mfc/reference/cfile-class.md#unlockrange)並未實作`CMemFile`。 如果您在上呼叫這些函式`CMemFile`物件，則將會收到[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。  
  
 `CMemFile`使用執行階段程式庫函式[malloc](../../c-runtime-library/reference/malloc.md)， [realloc](../../c-runtime-library/reference/realloc.md)，和[可用](../../c-runtime-library/reference/free.md)配置、 重新配置和解除配置的記憶體和內建[memcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md)區塊讀取和寫入時複製記憶體。 如果您想要變更此行為時`CMemFile`成長的檔案，衍生您自己從`CMemFile`並覆寫適當的函式。  
  
 如需有關`CMemFile`，請參閱文章[MFC 中的檔案](../../mfc/files-in-mfc.md)和[記憶體管理 (MFC)](../../mfc/memory-management.md)並查看[檔案處理](../../c-runtime-library/file-handling.md)中*執行階段程式庫參考*。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 `CMemFile`  
  
## <a name="requirements"></a>需求  
 **標頭：** afx.h  
  
##  <a name="alloc"></a>CMemFile::Alloc  
 會呼叫此函式`CMemFile`成員函式。  
  
```  
virtual BYTE* Alloc(SIZE_T nBytes);
```  
  
### <a name="parameters"></a>參數  
 `nBytes`  
 記憶體配置的位元組數目。  
  
### <a name="return-value"></a>傳回值  
 已配置的記憶體區塊的指標或**NULL**若配置失敗。  
  
### <a name="remarks"></a>備註  
 覆寫此函式以實作自訂的記憶體配置。 如果您覆寫這個函式，您可能會想要覆寫[免費](#free)和[Realloc](#realloc)以及。  
  
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
 以位元組為單位指定的緩衝區大小的整數。  
  
 `nGrowBytes`  
 以位元組為單位的記憶體配置遞增值。  
  
### <a name="remarks"></a>備註  
 這會導致`CMemFile`為記憶體檔案中使用的記憶體區塊。  
  
 如果`nGrowBytes`為 0，`CMemFile`將設定檔案長度為`nBufferSize`。 這表示，記憶體區塊中的資料之前已附加至`CMemFile`用作檔案。 以這種方式建立記憶體檔案無法成長。  
  
 由於檔案無法增長，小心不要造成`CMemFile`嘗試將檔案成長的。 例如，請勿呼叫`CMemFile`覆寫的[CFile:Write](../../mfc/reference/cfile-class.md#write)來寫入結尾，或不要呼叫[CFile:SetLength](../../mfc/reference/cfile-class.md#setlength)長度超過`nBufferSize`。  
  
 如果`nGrowBytes`大於 0，`CMemFile`將會忽略已連接的記憶體區塊的內容。 您必須從臨時使用寫入記憶體檔案的內容`CMemFile`覆寫`CFile::Write`。 如果您嘗試寫入超過檔案結尾，或檔案成長的藉由呼叫`CMemFile`覆寫`CFile::SetLength`，`CMemFile`會成長量的記憶體配置`nGrowBytes`。 如果您傳遞給記憶體區塊成長的記憶體配置將會失敗**附加**未與相容的方法以配置[配置](#alloc)。 預設實作與`Alloc`，您必須配置的記憶體與執行階段程式庫函式[malloc](../../c-runtime-library/reference/malloc.md)或[calloc](../../c-runtime-library/reference/calloc.md)。  
  
##  <a name="cmemfile"></a>CMemFile::CMemFile  
 第一個多載開啟空白記憶體檔案。  
  
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
 整數，指定檔案緩衝區大小，以位元組為單位。  
  
### <a name="remarks"></a>備註  
 請注意，建構函式開啟的檔案，您不應該呼叫[CFile::Open](../../mfc/reference/cfile-class.md#open)。  
  
 第二個多載作用相同時，如果您使用的第一個建構函式，並立即呼叫[附加](#attach)具有相同參數。 請參閱**附加**以取得詳細資料。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCFiles # 36](../../atl-mfc-shared/reference/codesnippet/cpp/cmemfile-class_1.cpp)]  
  
##  <a name="detach"></a>CMemFile::Detach  
 呼叫此函式可取得正在使用的記憶體區塊的指標`CMemFile`。  
  
```  
BYTE* Detach();
```  
  
### <a name="return-value"></a>傳回值  
 包含記憶體檔案的內容的記憶體區塊指標。  
  
### <a name="remarks"></a>備註  
 呼叫此函式也會關閉`CMemFile`。 您可以將記憶體區塊重新附加`CMemFile`藉由呼叫[附加](#attach)。 如果您想要重新附加檔案，並將資料用於，您應該呼叫[CFile::GetLength](../../mfc/reference/cfile-class.md#getlength)要取得其長度的檔案，然後再呼叫**卸離**。 請注意，如果您附加至的記憶體區塊`CMemFile`以便您可以使用它的資料 ( `nGrowBytes` = = 0)，則您將無法檔案成長的記憶體。  
  
##  <a name="free"></a>CMemFile::Free  
 會呼叫此函式`CMemFile`成員函式。  
  
```  
virtual void Free(BYTE* lpMem);
```  
  
### <a name="parameters"></a>參數  
 `lpMem`  
 要取消配置的記憶體指標。  
  
### <a name="remarks"></a>備註  
 覆寫此函式以實作自訂記憶體解除配置。 如果您覆寫這個函式，您可能會想要覆寫[配置](#alloc)和[Realloc](#realloc)也。  
  
##  <a name="growfile"></a>CMemFile::GrowFile  
 此函式呼叫的數個`CMemFile`成員函式。  
  
```  
virtual void GrowFile(SIZE_T dwNewLen);
```  
  
### <a name="parameters"></a>參數  
 `dwNewLen`  
 新的記憶體檔案的大小。  
  
### <a name="remarks"></a>備註  
 您可以覆寫它如果您想要變更如何`CMemFile`成長的檔案。 預設實作會呼叫[Realloc](#realloc)成長現有區塊 (或[配置](#alloc)建立的記憶體區塊)，配置記憶體的倍數`nGrowBytes`建構函式中指定的值或[附加](#attach)呼叫。  
  
##  <a name="memcpy"></a>CMemFile::Memcpy  
 會呼叫此函式`CMemFile`覆寫的[CFile::Read](../../mfc/reference/cfile-class.md#read)和[CFile::Write](../../mfc/reference/cfile-class.md#write)來傳輸資料的記憶體檔。  
  
```  
virtual BYTE* Memcpy(
    BYTE* lpMemTarget,  
    const BYTE* lpMemSource,  
    SIZE_T nBytes);
```  
  
### <a name="parameters"></a>參數  
 `lpMemTarget`  
 記憶體區塊，將複製的來源記憶體指標。  
  
 `lpMemSource`  
 來源的記憶體區塊指標。  
  
 `nBytes`  
 要複製的位元組數目。  
  
### <a name="return-value"></a>傳回值  
 `lpMemTarget` 的複本。  
  
### <a name="remarks"></a>備註  
 如果您想要變更的方式，覆寫此函數的`CMemFile`沒有這些記憶體複本。  
  
##  <a name="realloc"></a>CMemFile::Realloc  
 會呼叫此函式`CMemFile`成員函式。  
  
```  
virtual BYTE* Realloc(
    BYTE* lpMem,  
    SIZE_T nBytes);
```  
  
### <a name="parameters"></a>參數  
 `lpMem`  
 要重新配置的記憶體區塊指標。  
  
 `nBytes`  
 新的記憶體區塊大小。  
  
### <a name="return-value"></a>傳回值  
 已重新配置 （而且可能是移動），記憶體區塊的指標或**NULL**如果重新配置失敗。  
  
### <a name="remarks"></a>備註  
 覆寫此函式以實作自訂的記憶體配置。 如果您覆寫這個函式，您可能會想要覆寫[配置](#alloc)和[免費](#free)也。  
  
## <a name="see-also"></a>另請參閱  
 [CFile 類別](../../mfc/reference/cfile-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)




