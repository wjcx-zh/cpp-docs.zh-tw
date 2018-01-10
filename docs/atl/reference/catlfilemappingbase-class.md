---
title: "CAtlFileMappingBase 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlFileMappingBase
- ATLFILE/ATL::CAtlFileMappingBase
- ATLFILE/ATL::CAtlFileMappingBase::CAtlFileMappingBase
- ATLFILE/ATL::CAtlFileMappingBase::CopyFrom
- ATLFILE/ATL::CAtlFileMappingBase::GetData
- ATLFILE/ATL::CAtlFileMappingBase::GetHandle
- ATLFILE/ATL::CAtlFileMappingBase::GetMappingSize
- ATLFILE/ATL::CAtlFileMappingBase::MapFile
- ATLFILE/ATL::CAtlFileMappingBase::MapSharedMem
- ATLFILE/ATL::CAtlFileMappingBase::OpenMapping
- ATLFILE/ATL::CAtlFileMappingBase::Unmap
dev_langs: C++
helpviewer_keywords: CAtlFileMappingBase class
ms.assetid: be555723-2790-4f57-a8fb-be4d68460775
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4b5e0dd90894e052d4b9bcff08e7e12234dde8f4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="catlfilemappingbase-class"></a>CAtlFileMappingBase 類別
此類別代表的記憶體對應檔。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class CAtlFileMappingBase
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase)|建構函式。|  
|[CAtlFileMappingBase:: ~ CAtlFileMappingBase](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CAtlFileMappingBase::CopyFrom](#copyfrom)|呼叫此方法以複製的檔案對應物件。|  
|[CAtlFileMappingBase::GetData](#getdata)|呼叫此方法以從檔案對應物件取得資料。|  
|[CAtlFileMappingBase::GetHandle](#gethandle)|呼叫此方法以傳回的檔案控制代碼。|  
|[CAtlFileMappingBase::GetMappingSize](#getmappingsize)|呼叫這個方法，從檔案對應物件中取得對應大小。|  
|[CAtlFileMappingBase::MapFile](#mapfile)|呼叫這個方法來建立檔案對應物件。|  
|[CAtlFileMappingBase::MapSharedMem](#mapsharedmem)|呼叫這個方法來建立檔案對應物件，可讓您完整存取所有處理程序。|  
|[CAtlFileMappingBase::OpenMapping](#openmapping)|呼叫此方法以傳回檔案對應物件的控制代碼。|  
|[CAtlFileMappingBase::Unmap](#unmap)|呼叫這個方法來取消對應檔案對應物件。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CAtlFileMappingBase::operator =](#operator_eq)|目前的檔案對應物件設定為另一個檔案對應物件。|  
  
## <a name="remarks"></a>備註  
 檔案對應是檔案的內容與關聯的處理序的虛擬位址空間的一部分。 這個類別會提供方法來建立檔案對應物件，允許程式輕鬆地存取和共用資料。  
  
 如需詳細資訊，請參閱[檔案對應](http://msdn.microsoft.com/library/windows/desktop/aa366556)Windows SDK 中。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlfile.h  
  
##  <a name="catlfilemappingbase"></a>CAtlFileMappingBase::CAtlFileMappingBase  
 建構函式。  
  
```
CAtlFileMappingBase(CAtlFileMappingBase& orig);  
CAtlFileMappingBase() throw();
```  
  
### <a name="parameters"></a>參數  
 `orig`  
 若要建立新的物件複製原始的檔案對應物件。  
  
### <a name="remarks"></a>備註  
 建立新的檔案對應物件，您可以選擇使用現有的物件。 仍然必須呼叫[CAtlFileMappingBase::MapFile](#mapfile)開啟或建立特定檔案的檔案對應物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#71](../../atl/codesnippet/cpp/catlfilemappingbase-class_1.cpp)]  
  
##  <a name="dtor"></a>CAtlFileMappingBase:: ~ CAtlFileMappingBase  
 解構函式。  
  
```
~CAtlFileMappingBase() throw();
```  
  
### <a name="remarks"></a>備註  
 會釋放所有資源配置的類別並呼叫[CAtlFileMappingBase::Unmap](#unmap)方法。  
  
##  <a name="copyfrom"></a>CAtlFileMappingBase::CopyFrom  
 呼叫此方法以複製的檔案對應物件。  
  
```
HRESULT CopyFrom(CAtlFileMappingBase& orig) throw();
```  
  
### <a name="parameters"></a>參數  
 `orig`  
 要複製的原始的檔案對應物件。  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功或錯誤`HRESULT`失敗。  
  
##  <a name="getdata"></a>CAtlFileMappingBase::GetData  
 呼叫此方法以從檔案對應物件取得資料。  
  
```
void* GetData() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回資料的指標。  
  
##  <a name="gethandle"></a>CAtlFileMappingBase::GetHandle  
 呼叫此方法以傳回檔案對應物件的控制代碼。  
  
```
HANDLE GetHandle() throw ();
```  
  
### <a name="return-value"></a>傳回值  
 傳回檔案對應物件的控制代碼。  
  
##  <a name="getmappingsize"></a>CAtlFileMappingBase::GetMappingSize  
 呼叫這個方法，從檔案對應物件中取得對應大小。  
  
```
SIZE_T GetMappingSize() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回對應大小。  
  
### <a name="example"></a>範例  
 請參閱範例的[CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase)。  
  
##  <a name="mapfile"></a>CAtlFileMappingBase::MapFile  
 呼叫這個方法來開啟或建立檔案對應物件，為指定的檔案。  
  
```
HRESULT MapFile(
    HANDLE hFile,
    SIZE_T nMappingSize = 0,
    ULONGLONG nOffset = 0,
    DWORD dwMappingProtection = PAGE_READONLY,
    DWORD dwViewDesiredAccess = FILE_MAP_READ) throw();
```  
  
### <a name="parameters"></a>參數  
 `hFile`  
 要從中建立對應物件的檔案控制代碼。 `hFile`必須有效，而且不能設定為 INVALID_HANDLE_VALUE。  
  
 `nMappingSize`  
 對應的大小。 如果為 0，檔案對應物件的大小上限等於所識別的檔案的目前大小*hFile。*  
  
 `nOffset`  
 對應是要開始檔案位移。 位移的值必須是系統的記憶體配置資料粒度的倍數。  
  
 `dwMappingProtection`  
 保護所需要的檔案檢視對應檔。 請參閱`flProtect`中[CreateFileMapping](http://msdn.microsoft.com/library/windows/desktop/aa366537) Windows SDK 中。  
  
 `dwViewDesiredAccess`  
 指定存取檔案檢視，因此，對應的分頁檔案的保護類型。 請參閱`dwDesiredAccess`中[mapviewoffileex 在](http://msdn.microsoft.com/library/windows/desktop/aa366763)Windows SDK 中。  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功或錯誤`HRESULT`失敗。  
  
### <a name="remarks"></a>備註  
 建立檔案對應物件之後，檔案的大小不得超過檔案對應物件; 的大小若是如此，並非所有檔案的內容將可供共用。 如需詳細資訊，請參閱[CreateFileMapping](http://msdn.microsoft.com/library/windows/desktop/aa366537)和[mapviewoffileex 在](http://msdn.microsoft.com/library/windows/desktop/aa366763)Windows SDK 中。  
  
### <a name="example"></a>範例  
 請參閱範例的[CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase)。  
  
##  <a name="mapsharedmem"></a>CAtlFileMappingBase::MapSharedMem  
 呼叫這個方法來建立檔案對應物件，可讓您完整存取所有處理程序。  
  
```
HRESULT MapSharedMem(
    SIZE_T nMappingSize,
    LPCTSTR szName,
    BOOL* pbAlreadyExisted = NULL,
    LPSECURITY_ATTRIBUTES lpsa = NULL,
    DWORD dwMappingProtection = PAGE_READWRITE,
    DWORD dwViewDesiredAccess = FILE_MAP_ALL_ACCESS) throw();
```  
  
### <a name="parameters"></a>參數  
 `nMappingSize`  
 對應的大小。 如果為 0，檔案對應物件的大小上限等於所識別的檔案對應物件的目前大小`szName.`  
  
 `szName`  
 對應物件的名稱。  
  
 *pbAlreadyExisted*  
 指向 BOOL 值設為 TRUE，否則對應物件已經存在。  
  
 `lpsa`  
 將指標**ATTRIBUTES**結構，決定子處理序是否可以繼承傳回的控制代碼。 請參閱*lpAttributes*中[CreateFileMapping](http://msdn.microsoft.com/library/windows/desktop/aa366537) Windows SDK 中。  
  
 `dwMappingProtection`  
 在對應檔案時，檔案檢視中，想要保護。 請參閱`flProtect`中**CreateFileMapping** Windows SDK 中。  
  
 `dwViewDesiredAccess`  
 指定存取檔案檢視，因此，對應的分頁檔案的保護類型。 請參閱`dwDesiredAccess`中[mapviewoffileex 在](http://msdn.microsoft.com/library/windows/desktop/aa366763)Windows SDK 中。  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功或錯誤`HRESULT`失敗。  
  
### <a name="remarks"></a>備註  
 **MapShareMem**可讓現有的檔案對應物件，由[CreateFileMapping](http://msdn.microsoft.com/library/windows/desktop/aa366537)，以處理序之間共用。  
  
##  <a name="openmapping"></a>CAtlFileMappingBase::OpenMapping  
 呼叫這個方法，以開啟具名的檔案對應物件，為指定的檔案。  
  
```
HRESULT OpenMapping(
    LPCTSTR szName,
    SIZE_T nMappingSize,
    ULONGLONG nOffset = 0,
    DWORD dwViewDesiredAccess = FILE_MAP_ALL_ACCESS) throw();
```  
  
### <a name="parameters"></a>參數  
 `szName`  
 對應物件的名稱。 如果沒有這個名稱的檔案對應物件的開啟控制代碼，而且對應物件的安全性描述元未與衝突`dwViewDesiredAccess`參數，開啟作業成功。  
  
 `nMappingSize`  
 對應的大小。 如果為 0，檔案對應物件的大小上限等於所識別的檔案對應物件的目前大小`szName.`  
  
 `nOffset`  
 對應是要開始檔案位移。 位移的值必須是系統的記憶體配置資料粒度的倍數。  
  
 `dwViewDesiredAccess`  
 指定存取檔案檢視，因此，對應的分頁檔案的保護類型。 請參閱`dwDesiredAccess`中[mapviewoffileex 在](http://msdn.microsoft.com/library/windows/desktop/aa366763)Windows SDK 中。  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功或錯誤`HRESULT`失敗。  
  
### <a name="remarks"></a>備註  
 在偵錯組建中，如果輸入的參數無效，會發生判斷提示錯誤。  
  
##  <a name="operator_eq"></a>CAtlFileMappingBase::operator =  
 目前的檔案對應物件設定為另一個檔案對應物件。  
  
```
CAtlFileMappingBase& operator=(CAtlFileMappingBase& orig);
```  
  
### <a name="parameters"></a>參數  
 `orig`  
 目前的檔案對應物件。  
  
### <a name="return-value"></a>傳回值  
 傳回目前物件的參考。  
  
##  <a name="unmap"></a>CAtlFileMappingBase::Unmap  
 呼叫這個方法來取消對應檔案對應物件。  
  
```
HRESULT Unmap() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功或錯誤`HRESULT`失敗。  
  
### <a name="remarks"></a>備註  
 請參閱[unmapviewoffile 在](http://msdn.microsoft.com/library/windows/desktop/aa366882)更多詳細資料的 Windows SDK 中。  
  
## <a name="see-also"></a>請參閱  
 [CAtlFileMapping 類別](../../atl/reference/catlfilemapping-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)
