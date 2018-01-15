---
title: "CSharedFile 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSharedFile
- AFXADV/CSharedFile
- AFXADV/CSharedFile::CSharedFile
- AFXADV/CSharedFile::Detach
- AFXADV/CSharedFile::SetHandle
dev_langs: C++
helpviewer_keywords:
- CSharedFile [MFC], CSharedFile
- CSharedFile [MFC], Detach
- CSharedFile [MFC], SetHandle
ms.assetid: 5d000422-9ede-4318-a8c9-f7412b674f39
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 27c749f86f9e3fbd310fd03b3a82768d58632087
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="csharedfile-class"></a>CSharedFile 類別
[CMemFile](../../mfc/reference/cmemfile-class.md)-衍生的類別可支援共用記憶體檔案。  
  
## <a name="syntax"></a>語法  
  
```  
class CSharedFile : public CMemFile  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CSharedFile::CSharedFile](#csharedfile)|建構 `CSharedFile` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CSharedFile::Detach](#detach)|關閉共用的記憶體檔案，並傳回其記憶體區塊的控制代碼。|  
|[CSharedFile::SetHandle](#sethandle)|將共用的記憶體檔案附加至的記憶體區塊。|  
  
## <a name="remarks"></a>備註  
 不同之處在於檔案會儲存在 RAM 中，而不是磁碟上檔案的記憶體的行為與磁碟檔案。 記憶體檔案有助於快速暫存儲存位置或傳送未經處理位元組或序列化的獨立處理序之間的物件。  
  
 共用的記憶體檔案與不同的其他記憶體檔案，記憶體配置與[GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574) Windows 函式。 `CSharedFile`類別將資料儲存在全域配置的記憶體區塊 (使用建立**GlobalAlloc**)，並能夠使用 DDE、 剪貼簿或其他 OLE/COM 制式資料傳輸作業，例如，共用此記憶體區塊使用`IDataObject`。  
  
 **GlobalAlloc**傳回`HGLOBAL`處理而不是記憶體中，例如指標所傳回的指標[malloc](../../c-runtime-library/reference/malloc.md)。 `HGLOBAL`中某些應用程式需要控制代碼。 例如，若要將資料放剪貼簿您需要`HGLOBAL`處理。  
  
 請注意，`CSharedFile`不使用記憶體對應檔，並在處理序之間無法直接共用的資料。  
  
 `CSharedFile`物件可以自動配置自己的記憶體，或者您可以將附加到您自己的記憶體區塊`CSharedFile`藉由呼叫物件[CSharedFile::SetHandle](#sethandle)。 在任一情況下，自動成長的記憶體檔案的記憶體配置中`nGrowBytes`-如果大小為增量單位`nGrowBytes`不是零。  
  
 如需詳細資訊，請參閱文章[MFC 中的檔案](../../mfc/files-in-mfc.md)和[檔案處理](../../c-runtime-library/file-handling.md)中*執行階段程式庫參考*。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [CMemFile](../../mfc/reference/cmemfile-class.md)  
  
 `CSharedFile`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxadv.h  
  
##  <a name="csharedfile"></a>CSharedFile::CSharedFile  
 建構`CSharedFile`物件，並為它配置記憶體。  
  
```  
CSharedFile(
    UINT nAllocFlags = GMEM_DDESHARE | GMEM_MOVEABLE,  
    UINT nGrowBytes = 4096);
```  
  
### <a name="parameters"></a>參數  
 *nAllocFlags*  
 指出記憶體的配置方式的旗標。 請參閱[GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574)有效旗標值的清單。  
  
 `nGrowBytes`  
 以位元組為單位的記憶體配置遞增值。  
  
##  <a name="detach"></a>CSharedFile::Detach  
 呼叫此函式可關閉記憶體檔案，並中斷的記憶體區塊。  
  
```  
HGLOBAL Detach();
```  
  
### <a name="return-value"></a>傳回值  
 記憶體區塊，其中包含記憶體檔案的內容的控制代碼。  
  
### <a name="remarks"></a>備註  
 您可以藉由呼叫重新開啟它[sethandle，然後](#sethandle)，使用所傳回的控制代碼**卸離**。  
  
##  <a name="sethandle"></a>CSharedFile::SetHandle  
 呼叫此函式可附加的全域記憶體區塊`CSharedFile`物件。  
  
```  
void SetHandle(
    HGLOBAL hGlobalMemory,  
    BOOL bAllowGrow = TRUE);
```  
  
### <a name="parameters"></a>參數  
 *hGlobalMemory*  
 要附加至的全域記憶體處理`CSharedFile`。  
  
 `bAllowGrow`  
 指定的記憶體區塊是否可以成長。  
  
### <a name="remarks"></a>備註  
 如果`bAllowGrow`是非零值，記憶體區塊的大小增加為有需要，例如，如果嘗試對多個位元組寫入檔案時要比配置記憶體區塊。  
  
## <a name="see-also"></a>請參閱  
 [CMemFile 類別](../../mfc/reference/cmemfile-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CMemFile 類別](../../mfc/reference/cmemfile-class.md)
