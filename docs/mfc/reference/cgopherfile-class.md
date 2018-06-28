---
title: CGopherFile 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CGopherFile
- AFXINET/CGopherFile
- AFXINET/CGopherFile::CGopherFile
dev_langs:
- C++
helpviewer_keywords:
- CGopherFile [MFC], CGopherFile
ms.assetid: 3ca9898f-8cdb-4495-bbde-46d40100feda
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 275c35c7654f9a10a83f13482ca6d81b974c0dd6
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37040970"
---
# <a name="cgopherfile-class"></a>CGopherFile 類別
提供在 Gopher 伺服器上尋找和讀取檔案的功能。  
  
> [!NOTE]
>  類別`CGopherConnection`， `CGopherFile`， `CGopherFileFind`，`CGopherLocator`及它們的成員已被取代，因為它們無法在 Windows XP 平台運作，但他們仍會繼續在舊版平台上運作。  
  
## <a name="syntax"></a>語法  
  
```  
class CGopherFile : public CInternetFile  
```  
  
## <a name="members"></a>成員  
  
### <a name="protected-constructors"></a>受保護的建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CGopherFile::CGopherFile](#cgopherfile)|建構 `CGopherFile` 物件。|  
  
## <a name="remarks"></a>備註  
 Gopher 服務不允許使用者將資料寫入至 gopher 檔案，因為這項服務主要是做為找出資訊的功能表導向介面。 `CGopherFile`成員函式`Write`， `WriteString`，和`Flush`並未實作`CGopherFile`。 呼叫這些函式上`CGopherFile`物件，會傳回[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。  
  
 若要深入了解如何`CGopherFile`運作方式與其他 MFC 網際網路類別，請參閱文章[網際網路程式設計 WinInet](../../mfc/win32-internet-extensions-wininet.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [Cgopherfile](../../mfc/reference/cstdiofile-class.md)  
  
 [CInternetFile](../../mfc/reference/cinternetfile-class.md)  
  
 `CGopherFile`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxinet.h  
  
##  <a name="cgopherfile"></a>  CGopherFile::CGopherFile  
 呼叫此成員函式會建構`CGopherFile`物件。  
  
```  
CGopherFile(
    HINTERNET hFile,  
    CGopherLocator& refLocator,  
    CGopherConnection* pConnection);

 
CGopherFile(
    HINTERNET hFile,  
    HINTERNET hSession,  
    LPCTSTR pstrLocator,  
    DWORD dwLocLen,  
    DWORD_PTR dwContext);
```  
  
### <a name="parameters"></a>參數  
 *hFile*  
 控制代碼`HINTERNET`檔案。  
  
 *refLocator*  
 若要參考[CGopherLocator](../../mfc/reference/cgopherlocator-class.md)物件。  
  
 *pConnection*  
 指標[CGopherConnection](../../mfc/reference/cgopherconnection-class.md)物件。  
  
 *hSession*  
 目前的網際網路工作階段控制代碼。  
  
 *pstrLocator*  
 用來找出 gopher 伺服器的字串指標。 請參閱[Gopher 工作階段](cgopherlocator-class.md)如需有關 gopher 定位器。  
  
 *dwLocLen*  
 包含中的位元組數目為 DWORD *pstrLocator*。  
  
 *dwContext*  
 正在開啟之檔案的內容識別碼指標。  
  
### <a name="remarks"></a>備註  
 您需要`CGopherFile`gopher 的網際網路工作階段期間從檔案讀取物件。  
  
 您絕對不要建立`CGopherFile`直接物件。 請改為呼叫[CGopherConnection::OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile)開啟 gopher 伺服器上的檔案。  
  
## <a name="see-also"></a>另請參閱  
 [CInternetFile 類別](../../mfc/reference/cinternetfile-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CInternetFile 類別](../../mfc/reference/cinternetfile-class.md)   
 [CGopherLocator 類別](../../mfc/reference/cgopherlocator-class.md)   
 [CGopherFileFind 類別](../../mfc/reference/cgopherfilefind-class.md)   
 [CGopherConnection 類別](../../mfc/reference/cgopherconnection-class.md)
