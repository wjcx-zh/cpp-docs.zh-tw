---
title: "CGopherLocator 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CGopherLocator
- AFXINET/CGopherLocator
- AFXINET/CGopherLocator::CGopherLocator
- AFXINET/CGopherLocator::GetLocatorType
dev_langs:
- C++
helpviewer_keywords:
- gopher locator
- CGopherLocator class
- Internet, gopher searches
ms.assetid: 6fcc015f-5ae6-4959-b936-858634c71019
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
ms.openlocfilehash: c5c9b862714d046bc81a49dda27fd5fc062b9ba8
ms.lasthandoff: 02/24/2017

---
# <a name="cgopherlocator-class"></a>CGopherLocator 類別
從 gopher 伺服器取得 gopher 「 定位器 」，判斷定位器的類型，並讓定位器[CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)。  
  
> [!NOTE]
>  類別`CGopherConnection`， `CGopherFile`， `CGopherFileFind`，`CGopherLocator`和其成員已被取代，因為無法在 Windows XP 平台上運作，但它們會繼續在舊版平台上運作。  
  
## <a name="syntax"></a>語法  
  
```  
class CGopherLocator : public CObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CGopherLocator::CGopherLocator](#cgopherlocator)|建構 `CGopherLocator` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CGopherLocator::GetLocatorType](#getlocatortype)|剖析 gopher 定位器，並判斷其屬性。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CGopherLocator::operator LPCTSTR](#operator_lpctstr)|直接存取儲存在字元`CGopherLocator`物件做為 C 樣式的字串。|  
  
## <a name="remarks"></a>備註  
 它可以從伺服器擷取資訊之前，應用程式必須取得 gopher 伺服器定位器。 一旦擁有定位器，它必須將定位器視為不透明的語彙基元。  
  
 每個 gopher 定位器已決定的檔案或找到的伺服器類型的屬性。 請參閱[GetLocatorType](#getlocatortype) gopher 定位器類型的清單。  
  
 應用程式通常使用定位器呼叫[CGopherFileFind::FindFile](../../mfc/reference/cgopherfilefind-class.md#findfile)來擷取特定資訊。  
  
 若要深入了解如何`CGopherLocator`運作方式與其他 MFC 網際網路類別，請參閱文章[網際網路程式設計 WinInet](../../mfc/win32-internet-extensions-wininet.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CGopherLocator`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxinet.h  
  
##  <a name="cgopherlocator"></a>CGopherLocator::CGopherLocator  
 此成員函式會呼叫建立`CGopherLocator`物件。  
  
```  
CGopherLocator(const CGopherLocator& ref);
```  
  
### <a name="parameters"></a>參數  
 `ref`  
 常數的參考`CGopherLocator`物件。  
  
### <a name="remarks"></a>備註  
 絕對不要建立`CGopherLocator`直接物件。 請改為呼叫[CGopherConnection::CreateLocator](../../mfc/reference/cgopherconnection-class.md#createlocator)建立並傳回一個指向`CGopherLocator`物件。  
  
##  <a name="getlocatortype"></a>CGopherLocator::GetLocatorType  
 呼叫此成員函式，以取得定位器類型。  
  
```  
BOOL GetLocatorType(DWORD& dwRef) const;  
```  
  
### <a name="parameters"></a>參數  
 *dwRef*  
 參考`DWORD`，將會收到定位器類型。 請參閱**備註**定位器類型的資料表。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。 如果呼叫失敗，Win32 函式[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)可能呼叫以判斷錯誤的原因。  
  
### <a name="remarks"></a>備註  
 可能的類型如下所示︰  
  
|值|意義|  
|-----------|-------------|  
|GOPHER_TYPE_TEXT_FILE|ASCII 文字檔案。|  
|GOPHER_TYPE_DIRECTORY|其他 Gopher 項目的目錄。|  
|GOPHER_TYPE_CSO|CSO 電話簿伺服器。|  
|GOPHER_TYPE_ERROR|指出錯誤狀況。|  
|GOPHER_TYPE_MAC_BINHEX|Macintosh 的 BINHEX 格式檔案。|  
|GOPHER_TYPE_DOS_ARCHIVE|DOS 封存檔。|  
|GOPHER_TYPE_UNIX_UUENCODED|使用 uuencode 編碼檔案。|  
|GOPHER_TYPE_INDEX_SERVER|索引伺服器。|  
|GOPHER_TYPE_TELNET|Telnet 伺服器。|  
|GOPHER_TYPE_BINARY|二進位檔案。|  
|GOPHER_TYPE_REDUNDANT|重複的伺服器。 中包含的資訊是主要伺服器的複本。 主要伺服器，則沒有 GOPHER_TYPE_REDUNDANT 類型的最後一個目錄項目。|  
|GOPHER_TYPE_TN3270|TN3270 伺服器。|  
|GOPHER_TYPE_GIF|GIF 圖形檔案。|  
|GOPHER_TYPE_IMAGE|影像檔。|  
|GOPHER_TYPE_BITMAP|點陣圖檔案。|  
|GOPHER_TYPE_MOVIE|影片檔。|  
|GOPHER_TYPE_SOUND|音效檔。|  
|GOPHER_TYPE_HTML|HTML 文件。|  
|GOPHER_TYPE_PDF|PDF 檔案。|  
|GOPHER_TYPE_CALENDAR|行事曆檔案。|  
|GOPHER_TYPE_INLINE|內嵌檔。|  
|GOPHER_TYPE_UNKNOWN|未知的項目類型。|  
|GOPHER_TYPE_ASK|詢問 + 項目。|  
|GOPHER_TYPE_GOPHER_PLUS|Gopher + 項目。|  
  
##  <a name="operator_lpctstr"></a>CGopherLocator::operator LPCTSTR  
 這個實用的轉型運算子提供一個有效的方法，以存取包含在 null 結束的 C 字串`CGopherLocator`物件。  
  
```  
operator LPCTSTR () const;  
```  
  
### <a name="return-value"></a>傳回值  
 字串資料的字元指標。  
  
### <a name="remarks"></a>備註  
 會不複製任何字元。只有指標會傳回。  
  
## <a name="see-also"></a>另請參閱  
 [CObject 類別](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CGopherFileFind 類別](../../mfc/reference/cgopherfilefind-class.md)

