---
title: "CGopherFile 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CGopherFile
dev_langs:
- C++
helpviewer_keywords:
- gopher protocol files
- Internet, gopher
- CGopherFile class
ms.assetid: 3ca9898f-8cdb-4495-bbde-46d40100feda
caps.latest.revision: 23
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
ms.openlocfilehash: 40c1e385d0f58095c2aa79cc23168fc00f48ed9b
ms.lasthandoff: 02/24/2017

---
# <a name="cgopherfile-class"></a>CGopherFile 類別
提供在 Gopher 伺服器上尋找和讀取檔案的功能。  
  
> [!NOTE]
>  類別`CGopherConnection`， `CGopherFile`， `CGopherFileFind`，`CGopherLocator`和其成員已被取代，因為無法在 Windows XP 平台上運作，但它們會繼續在舊版平台上運作。  
  
## <a name="syntax"></a>語法  
  
```  
class CGopherFile : public CInternetFile  
```  
  
## <a name="members"></a>Members  
  
### <a name="protected-constructors"></a>受保護的建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CGopherFile::CGopherFile](#cgopherfile)|建構 `CGopherFile` 物件。|  
  
## <a name="remarks"></a>備註  
 Gopher 服務不允許將資料寫入至 gopher 檔案，因為這項服務主要是做為功能表導向的介面，找出資訊的使用者。 `CGopherFile`成員函式**撰寫**， `WriteString`，和`Flush`並未實作`CGopherFile`。 呼叫這些函式上`CGopherFile`物件，會傳回[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。  
  
 若要深入了解如何`CGopherFile`運作方式與其他 MFC 網際網路類別，請參閱文章[網際網路程式設計 WinInet](../../mfc/win32-internet-extensions-wininet.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [Cgopherfile](../../mfc/reference/cstdiofile-class.md)  
  
 [CInternetFile](../../mfc/reference/cinternetfile-class.md)  
  
 `CGopherFile`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxinet.h  
  
##  <a name="a-namecgopherfilea--cgopherfilecgopherfile"></a><a name="cgopherfile"></a>CGopherFile::CGopherFile  
 此成員函式呼叫來建構`CGopherFile`物件。  
  
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
 `hFile`  
 控制代碼`HINTERNET`檔案。  
  
 `refLocator`  
 參考[CGopherLocator](../../mfc/reference/cgopherlocator-class.md)物件。  
  
 `pConnection`  
 指標[CGopherConnection](../../mfc/reference/cgopherconnection-class.md)物件。  
  
 `hSession`  
 目前的網際網路工作階段控制代碼。  
  
 `pstrLocator`  
 用來找出 gopher 伺服器的字串指標。 請參閱[Gopher 工作階段](https://msdn.microsoft.com/library/24wz8xze.aspx)如需有關 gopher 定位器。  
  
 *dwLocLen*  
 DWORD，其中包含數字中的位元組`pstrLocator`。  
  
 `dwContext`  
 正在開啟之檔案的內容識別碼指標。  
  
### <a name="remarks"></a>備註  
 您需要`CGopherFile`gopher 的網際網路工作階段期間從檔案讀取物件。  
  
 絕對不要建立`CGopherFile`直接物件。 請改為呼叫[CGopherConnection::OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile)至 gopher 伺服器上開啟檔案。  
  
## <a name="see-also"></a>另請參閱  
 [CInternetFile 類別](../../mfc/reference/cinternetfile-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CInternetFile 類別](../../mfc/reference/cinternetfile-class.md)   
 [CGopherLocator 類別](../../mfc/reference/cgopherlocator-class.md)   
 [CGopherFileFind 類別](../../mfc/reference/cgopherfilefind-class.md)   
 [CGopherConnection 類別](../../mfc/reference/cgopherconnection-class.md)

