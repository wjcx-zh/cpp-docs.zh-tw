---
title: "COleStreamFile 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleStreamFile
- AFXOLE/COleStreamFile
- AFXOLE/COleStreamFile::COleStreamFile
- AFXOLE/COleStreamFile::Attach
- AFXOLE/COleStreamFile::CreateMemoryStream
- AFXOLE/COleStreamFile::CreateStream
- AFXOLE/COleStreamFile::Detach
- AFXOLE/COleStreamFile::GetStream
- AFXOLE/COleStreamFile::OpenStream
dev_langs:
- C++
helpviewer_keywords:
- data streams [C++]
- streams [C++], OLE
- data streams [C++], OLE
- structured storage in OLE
- OLE structured storage [C++]
- OLE [C++], streams of data
- COleStreamFile class
ms.assetid: e4f93698-e17c-4a18-a7c0-4b4df8eb4d93
caps.latest.revision: 22
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
ms.openlocfilehash: 0840d365f4179da0ad680256688eaf9484cb3cd8
ms.lasthandoff: 02/24/2017

---
# <a name="colestreamfile-class"></a>COleStreamFile 類別
表示資料的資料流 ( `IStream`) 在複合檔案做為 OLE 結構化儲存體的一部分。  
  
## <a name="syntax"></a>語法  
  
```  
class COleStreamFile : public CFile  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[COleStreamFile::COleStreamFile](#colestreamfile)|建構 `COleStreamFile` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[COleStreamFile::Attach](#attach)|將資料流與物件相關聯。|  
|[COleStreamFile::CreateMemoryStream](#creatememorystream)|從全域記憶體中建立的資料流，並將它與物件相關聯。|  
|[COleStreamFile::CreateStream](#createstream)|建立資料流，並將它與物件相關聯。|  
|[COleStreamFile::Detach](#detach)|解除關聯之物件的資料流。|  
|[COleStreamFile::GetStream](#getstream)|傳回目前資料流。|  
|[COleStreamFile::OpenStream](#openstream)|安全地開啟資料流，並將它與物件相關聯。|  
  
## <a name="remarks"></a>備註  
 `IStorage`物件必須存在才能開啟或建立，除非它是記憶體資料流之資料流。  
  
 `COleStreamFile`物件完全相同的操作[CFile](../../mfc/reference/cfile-class.md)物件。  
  
 如需操作資料流與儲存的詳細資訊，請參閱文章[容器︰ 複合檔案](../../mfc/containers-compound-files.md)...  
  
 如需詳細資訊，請參閱[IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034)和[IStorage](http://msdn.microsoft.com/library/windows/desktop/aa380015)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 `COleStreamFile`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxole.h  
  
##  <a name="attach"></a>COleStreamFile::Attach  
 將使用提供的 OLE 資料流`COleStreamFile`物件。  
  
```  
void Attach(LPSTREAM lpStream);
```  
  
### <a name="parameters"></a>參數  
 `lpStream`  
 指向 OLE 資料流 ( `IStream`) 與物件相關聯。 不能是**NULL**。  
  
### <a name="remarks"></a>備註  
 物件已不可 OLE 資料流相關聯。  
  
 如需詳細資訊，請參閱[IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="colestreamfile"></a>COleStreamFile::COleStreamFile  
 建立 `COleStreamFile` 物件。  
  
```  
COleStreamFile(LPSTREAM lpStream = NULL);
```  
  
### <a name="parameters"></a>參數  
 `lpStream`  
 要與物件相關聯之 OLE 資料流指標。  
  
### <a name="remarks"></a>備註  
 如果`lpStream`是**NULL**、 物件並不是 OLE 資料流相關聯，否則該物件提供的 OLE 資料流相關聯。  
  
 如需詳細資訊，請參閱[IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="creatememorystream"></a>COleStreamFile::CreateMemoryStream  
 安全地建立新的資料流通用的共用記憶體不足其中失敗是正常且預期的情況。  
  
```  
BOOL CreateMemoryStream(CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>參數  
 `pError`  
 指向[CFileException](../../mfc/reference/cfileexception-class.md)物件或**NULL** ，表示建立作業的完成狀態。 如果您想要監視可能嘗試建立資料流所產生的例外狀況，請提供這個參數。  
  
### <a name="return-value"></a>傳回值  
 如果成功; 建立資料流，非零值。否則為 0。  
  
### <a name="remarks"></a>備註  
 由 OLE 子系統所配置的記憶體。  
  
 如需詳細資訊，請參閱[CreateStreamOnHGlobal](http://msdn.microsoft.com/library/windows/desktop/aa378980)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="createstream"></a>COleStreamFile::CreateStream  
 提供的儲存體物件，其中失敗是正常且預期的情況中，安全地建立新的資料流。  
  
```  
BOOL CreateStream(
    LPSTORAGE lpStorage,  
    LPCTSTR lpszStreamName,  
    DWORD nOpenFlags = modeReadWrite|shareExclusive|modeCreate,  
    CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>參數  
 `lpStorage`  
 包含要建立資料流 OLE 儲存物件的指標。 不能是**NULL**。  
  
 `lpszStreamName`  
 若要建立資料流名稱。 不能是**NULL**。  
  
 `nOpenFlags`  
 用來開啟資料流的存取模式。 獨佔、 讀取/寫入，並建立模式會使用預設值。 如需可用的模式的完整清單，請參閱[CFile::CFile](../../mfc/reference/cfile-class.md#cfile)。  
  
 `pError`  
 指向[CFileException](../../mfc/reference/cfileexception-class.md)物件或**NULL**。 如果您想要監視可能嘗試建立資料流所產生的例外狀況，請提供這個參數。  
  
### <a name="return-value"></a>傳回值  
 如果成功; 建立資料流，非零值。否則為 0。  
  
### <a name="remarks"></a>備註  
 如果無法開啟檔案的例外狀況將會擲回和`pError`不**NULL**。  
  
 如需詳細資訊，請參閱[IStorage::CreateStream](http://msdn.microsoft.com/library/windows/desktop/aa380020)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="detach"></a>COleStreamFile::Detach  
 解除關聯物件的資料流，而不需要關閉資料流。  
  
```  
LPSTREAM Detach();
```  
  
### <a name="return-value"></a>傳回值  
 資料流的指標 ( `IStream`) 是與物件相關聯。  
  
### <a name="remarks"></a>備註  
 程式終止之前，必須透過其他方式關閉資料流。  
  
 如需詳細資訊，請參閱[IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getstream"></a>COleStreamFile::GetStream  
 呼叫此函式來傳回目前資料流的指標。  
  
```  
IStream* GetStream() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前資料流介面的指標 ( [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034))。  
  
##  <a name="openstream"></a>COleStreamFile::OpenStream  
 開啟現有的資料流。  
  
```  
BOOL OpenStream(
    LPSTORAGE lpStorage,  
    LPCTSTR lpszStreamName,  
    DWORD nOpenFlags = modeReadWrite|shareExclusive,  
    CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>參數  
 `lpStorage`  
 包含要開啟的資料流的 OLE 儲存體物件的指標。 不能是**NULL**。  
  
 `lpszStreamName`  
 若要開啟資料流名稱。 不能是**NULL**。  
  
 `nOpenFlags`  
 用來開啟資料流的存取模式。 獨佔和讀/寫模式會使用預設值。 可用的模式的完整清單，請參閱[CFile::CFile](../../mfc/reference/cfile-class.md#cfile)。  
  
 `pError`  
 指向[CFileException](../../mfc/reference/cfileexception-class.md)物件或**NULL**。 如果您想要監視可能嘗試開啟資料流所產生的例外狀況，請提供這個參數。  
  
### <a name="return-value"></a>傳回值  
 如果成功，開啟資料流，則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 如果無法開啟檔案的例外狀況將會擲回和`pError`不**NULL**。  
  
 如需詳細資訊，請參閱[IStorage::OpenStream](http://msdn.microsoft.com/library/windows/desktop/aa380025)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [CFile 類別](../../mfc/reference/cfile-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)




