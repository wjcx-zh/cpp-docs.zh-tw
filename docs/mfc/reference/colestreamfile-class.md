---
title: COleStreamFile 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- COleStreamFile [MFC], COleStreamFile
- COleStreamFile [MFC], Attach
- COleStreamFile [MFC], CreateMemoryStream
- COleStreamFile [MFC], CreateStream
- COleStreamFile [MFC], Detach
- COleStreamFile [MFC], GetStream
- COleStreamFile [MFC], OpenStream
ms.assetid: e4f93698-e17c-4a18-a7c0-4b4df8eb4d93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7bbd2b19e85f70ae9e61044ccd5a6c369e61b296
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37041441"
---
# <a name="colestreamfile-class"></a>COleStreamFile 類別
表示資料的資料流 ( `IStream`) 在複合檔案中做為 OLE 結構化儲存體的一部分。  
  
## <a name="syntax"></a>語法  
  
```  
class COleStreamFile : public CFile  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[COleStreamFile::COleStreamFile](#colestreamfile)|建構 `COleStreamFile` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[COleStreamFile::Attach](#attach)|將資料流與物件產生關聯。|  
|[COleStreamFile::CreateMemoryStream](#creatememorystream)|從全域記憶體中建立的資料流，並將其與物件相關聯。|  
|[COleStreamFile::CreateStream](#createstream)|建立資料流，並將其與物件相關聯。|  
|[COleStreamFile::Detach](#detach)|解除關聯之物件的資料流。|  
|[COleStreamFile::GetStream](#getstream)|傳回目前資料流。|  
|[COleStreamFile::OpenStream](#openstream)|安全無虞地開啟資料流，並將其與物件相關聯。|  
  
## <a name="remarks"></a>備註  
 `IStorage`物件必須存在才能開啟或建立，除非它是記憶體資料流資料流。  
  
 `COleStreamFile` 物件完全一樣管理[CFile](../../mfc/reference/cfile-class.md)物件。  
  
 如需操作資料流與儲存的詳細資訊，請參閱文章[容器： 複合檔案](../../mfc/containers-compound-files.md)...  
  
 如需詳細資訊，請參閱[IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034)和[IStorage](http://msdn.microsoft.com/library/windows/desktop/aa380015) Windows SDK 中。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 `COleStreamFile`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxole.h  
  
##  <a name="attach"></a>  COleStreamFile::Attach  
 將具有提供的 OLE 資料流`COleStreamFile`物件。  
  
```  
void Attach(LPSTREAM lpStream);
```  
  
### <a name="parameters"></a>參數  
 *lpStream*  
 指向 OLE 資料流 ( `IStream`) 與物件相關聯。 不能**NULL**。  
  
### <a name="remarks"></a>備註  
 物件已經不得與 OLE 資料流相關聯。  
  
 如需詳細資訊，請參閱[IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) Windows SDK 中。  
  
##  <a name="colestreamfile"></a>  COleStreamFile::COleStreamFile  
 建立 `COleStreamFile` 物件。  
  
```  
COleStreamFile(LPSTREAM lpStream = NULL);
```  
  
### <a name="parameters"></a>參數  
 *lpStream*  
 要與物件相關聯之 OLE 資料流指標。  
  
### <a name="remarks"></a>備註  
 如果*lpStream*是**NULL**物件不是與 OLE 資料流相關聯，否則物件是提供的 OLE 資料流相關聯。  
  
 如需詳細資訊，請參閱[IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) Windows SDK 中。  
  
##  <a name="creatememorystream"></a>  COleStreamFile::CreateMemoryStream  
 安全地建立新的資料流通用的共用記憶體不足失敗所在的標準模式、 預期的條件。  
  
```  
BOOL CreateMemoryStream(CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>參數  
 *pError*  
 指向[CFileException](../../mfc/reference/cfileexception-class.md)物件或**NULL** ，表示建立作業的完成狀態。 如果您想要監視可能嘗試建立資料流所產生的例外狀況，請提供這個參數。  
  
### <a name="return-value"></a>傳回值  
 如果已成功; 建立資料流，則為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 配置的記憶體是由 OLE 子系統。  
  
 如需詳細資訊，請參閱[CreateStreamOnHGlobal](http://msdn.microsoft.com/library/windows/desktop/aa378980) Windows SDK 中。  
  
##  <a name="createstream"></a>  COleStreamFile::CreateStream  
 提供的儲存體物件失敗所在正常、 預期的狀況中，安全地建立新的資料流。  
  
```  
BOOL CreateStream(
    LPSTORAGE lpStorage,  
    LPCTSTR lpszStreamName,  
    DWORD nOpenFlags = modeReadWrite|shareExclusive|modeCreate,  
    CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>參數  
 *lpStorage*  
 指向包含要建立的資料流 OLE 儲存物件。 不能**NULL**。  
  
 *lpszStreamName*  
 若要建立資料流名稱。 不能**NULL**。  
  
 *nOpenFlags*  
 開啟資料流時要使用的存取模式。 獨佔，讀取/寫入，並建立模式由預設值。 如需可用的模式的完整清單，請參閱[CFile::CFile](../../mfc/reference/cfile-class.md#cfile)。  
  
 *pError*  
 指向[CFileException](../../mfc/reference/cfileexception-class.md)物件或**NULL**。 如果您想要監視可能嘗試建立資料流所產生的例外狀況，請提供這個參數。  
  
### <a name="return-value"></a>傳回值  
 如果已成功; 建立資料流，則為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 如果開啟作業失敗，則擲回檔案例外狀況和*pError*不**NULL**。  
  
 如需詳細資訊，請參閱[IStorage::CreateStream](http://msdn.microsoft.com/library/windows/desktop/aa380020) Windows SDK 中。  
  
##  <a name="detach"></a>  COleStreamFile::Detach  
 解除關聯物件的資料流，而不需要關閉資料流。  
  
```  
LPSTREAM Detach();
```  
  
### <a name="return-value"></a>傳回值  
 資料流的指標 ( `IStream`) 是與物件相關聯。  
  
### <a name="remarks"></a>備註  
 在程式終止之前，資料流必須先關閉其他方式。  
  
 如需詳細資訊，請參閱[IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) Windows SDK 中。  
  
##  <a name="getstream"></a>  COleStreamFile::GetStream  
 呼叫此函式可傳回目前資料流的指標。  
  
```  
IStream* GetStream() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前資料流介面的指標 ( [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034))。  
  
##  <a name="openstream"></a>  COleStreamFile::OpenStream  
 開啟現有的資料流。  
  
```  
BOOL OpenStream(
    LPSTORAGE lpStorage,  
    LPCTSTR lpszStreamName,  
    DWORD nOpenFlags = modeReadWrite|shareExclusive,  
    CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>參數  
 *lpStorage*  
 指向包含要開啟的資料流 OLE 儲存物件。 不能**NULL**。  
  
 *lpszStreamName*  
 若要開啟資料流名稱。 不能**NULL**。  
  
 *nOpenFlags*  
 開啟資料流時要使用的存取模式。 獨佔和讀/寫模式所使用預設值。 可用的模式的完整清單，請參閱[CFile::CFile](../../mfc/reference/cfile-class.md#cfile)。  
  
 *pError*  
 指向[CFileException](../../mfc/reference/cfileexception-class.md)物件或**NULL**。 如果您想要監視可能嘗試開啟資料流所產生的例外狀況，請提供這個參數。  
  
### <a name="return-value"></a>傳回值  
 如果成功; 開啟資料流，則為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 如果開啟作業失敗，則擲回檔案例外狀況和*pError*不**NULL**。  
  
 如需詳細資訊，請參閱[IStorage::OpenStream](http://msdn.microsoft.com/library/windows/desktop/aa380025) Windows SDK 中。  
  
## <a name="see-also"></a>另請參閱  
 [CFile 類別](../../mfc/reference/cfile-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)



