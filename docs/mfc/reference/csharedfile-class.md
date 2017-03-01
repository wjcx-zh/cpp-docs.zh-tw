---
title: "CSharedFile 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSharedFile
dev_langs:
- C++
helpviewer_keywords:
- memory files
- CSharedFile class
- shared memory files
ms.assetid: 5d000422-9ede-4318-a8c9-f7412b674f39
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: f812b2c7b8e3b158068bf3fdab0a327460056251
ms.lasthandoff: 02/24/2017

---
# <a name="csharedfile-class"></a>CSharedFile 類別
[CMemFile](../../mfc/reference/cmemfile-class.md)-衍生的類別可支援共用記憶體檔案。  
  
## <a name="syntax"></a>語法  
  
```  
class CSharedFile : public CMemFile  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CSharedFile::CSharedFile](#csharedfile)|建構 `CSharedFile` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CSharedFile::Detach](#detach)|關閉共用的記憶體檔案，並傳回其記憶體區塊的控制代碼。|  
|[CSharedFile::SetHandle](#sethandle)|將共用的記憶體檔案附加至的記憶體區塊。|  
  
## <a name="remarks"></a>備註  
 記憶體檔案的行為如同磁碟檔案不同之處在於檔案會儲存在 RAM 中，而不是在磁碟上。 記憶體檔案有助於快速暫時存放或傳輸未經處理位元組或序列化的物件之間獨立的處理序。  
  
 共用的記憶體檔案不同於其他記憶體檔案的記憶體配置與[GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574) Windows 函式。 `CSharedFile`類別會將資料儲存在全域配置的記憶體區塊 (使用建立**GlobalAlloc**)，而此記憶體區塊可以共用使用 DDE、 剪貼簿或其他 OLE/COM 制式資料傳輸作業，例如，使用`IDataObject`。  
  
 **GlobalAlloc**傳回`HGLOBAL`而不是記憶體，例如傳回的指標的指標處理[malloc](../../c-runtime-library/reference/malloc.md)。 `HGLOBAL`控制代碼所需的特定應用程式。 比方說，若要將資料放剪貼簿您需要`HGLOBAL`處理。  
  
 請注意，`CSharedFile`不使用記憶體對應檔，並在處理序之間無法直接共用的資料。  
  
 `CSharedFile`物件，可以自動配置它們自己的記憶體，或您可以將附加至您自己的記憶體區塊`CSharedFile`物件呼叫[CSharedFile::SetHandle](#sethandle)。 在任一情況下，自動成長的記憶體檔案的記憶體配置在`nGrowBytes`-如果大小遞增`nGrowBytes`不是零。  
  
 如需詳細資訊，請參閱文章[MFC 中的檔案](../../mfc/files-in-mfc.md)和[檔案處理](../../c-runtime-library/file-handling.md)中*執行階段程式庫參考*。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [CMemFile](../../mfc/reference/cmemfile-class.md)  
  
 `CSharedFile`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxadv.h  
  
##  <a name="a-namecsharedfilea--csharedfilecsharedfile"></a><a name="csharedfile"></a>CSharedFile::CSharedFile  
 建構`CSharedFile`物件，並為其配置記憶體。  
  
```  
CSharedFile(
    UINT nAllocFlags = GMEM_DDESHARE | GMEM_MOVEABLE,  
    UINT nGrowBytes = 4096);
```  
  
### <a name="parameters"></a>參數  
 *nAllocFlags*  
 旗標，指出要配置的記憶體的方式。 請參閱[GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574)有效旗標值的清單。  
  
 `nGrowBytes`  
 以位元組為單位的記憶體配置遞增值。  
  
##  <a name="a-namedetacha--csharedfiledetach"></a><a name="detach"></a>CSharedFile::Detach  
 呼叫此函式來關閉記憶體的檔案，並中斷的記憶體區塊。  
  
```  
HGLOBAL Detach();
```  
  
### <a name="return-value"></a>傳回值  
 記憶體區塊，其中包含記憶體檔案的內容的控制代碼。  
  
### <a name="remarks"></a>備註  
 您可以藉由呼叫重新開啟它[SetHandle](#sethandle)，使用傳回的控制代碼**卸離**。  
  
##  <a name="a-namesethandlea--csharedfilesethandle"></a><a name="sethandle"></a>CSharedFile::SetHandle  
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
 指定記憶體區塊是否可以成長。  
  
### <a name="remarks"></a>備註  
 如果`bAllowGrow`是非零值，記憶體區塊的大小增加為必要的比方說，如果嘗試對多個位元組寫入檔案時要比所配置的記憶體區塊。  
  
## <a name="see-also"></a>另請參閱  
 [CMemFile 類別](../../mfc/reference/cmemfile-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CMemFile 類別](../../mfc/reference/cmemfile-class.md)

