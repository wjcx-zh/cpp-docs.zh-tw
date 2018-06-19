---
title: CGopherLocator 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CGopherLocator
- AFXINET/CGopherLocator
- AFXINET/CGopherLocator::CGopherLocator
- AFXINET/CGopherLocator::GetLocatorType
dev_langs:
- C++
helpviewer_keywords:
- CGopherLocator [MFC], CGopherLocator
- CGopherLocator [MFC], GetLocatorType
ms.assetid: 6fcc015f-5ae6-4959-b936-858634c71019
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 377708108f96a42d23dcf3aa5e8214d7bf9ffe5c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33366918"
---
# <a name="cgopherlocator-class"></a>CGopherLocator 類別
從 gopher 伺服器取得 gopher 「 定位器 」，判斷定位器的類型，並將定位器提供給[CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)。  
  
> [!NOTE]
>  類別`CGopherConnection`， `CGopherFile`， `CGopherFileFind`，`CGopherLocator`及它們的成員已被取代，因為它們無法在 Windows XP 平台運作，但他們仍會繼續在舊版平台上運作。  
  
## <a name="syntax"></a>語法  
  
```  
class CGopherLocator : public CObject  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CGopherLocator::CGopherLocator](#cgopherlocator)|建構 `CGopherLocator` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CGopherLocator::GetLocatorType](#getlocatortype)|剖析 gopher 定位器，並判斷它的屬性。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CGopherLocator::operator LPCTSTR](#operator_lpctstr)|直接存取儲存在字元`CGopherLocator`物件做為 C 樣式字串。|  
  
## <a name="remarks"></a>備註  
 應用程式必須取得 gopher 伺服器定位器，再從該伺服器擷取資訊。 一旦有定位器，它必須在定位器視為不透明的語彙基元。  
  
 每個 gopher 定位器具有可判定檔案或伺服器找到的類型屬性。 請參閱[GetLocatorType](#getlocatortype)取得一份 gopher 定位器的類型。  
  
 應用程式通常使用定位器的呼叫[CGopherFileFind::FindFile](../../mfc/reference/cgopherfilefind-class.md#findfile)擷取特定資訊。  
  
 若要深入了解如何`CGopherLocator`運作方式與其他 MFC 網際網路類別，請參閱文章[網際網路程式設計 WinInet](../../mfc/win32-internet-extensions-wininet.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CGopherLocator`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxinet.h  
  
##  <a name="cgopherlocator"></a>  CGopherLocator::CGopherLocator  
 此成員函式呼叫以建立`CGopherLocator`物件。  
  
```  
CGopherLocator(const CGopherLocator& ref);
```  
  
### <a name="parameters"></a>參數  
 `ref`  
 常數的參考`CGopherLocator`物件。  
  
### <a name="remarks"></a>備註  
 您絕對不要建立`CGopherLocator`直接物件。 請改為呼叫[CGopherConnection::CreateLocator](../../mfc/reference/cgopherconnection-class.md#createlocator)來建立並傳回的指標`CGopherLocator`物件。  
  
##  <a name="getlocatortype"></a>  CGopherLocator::GetLocatorType  
 呼叫此成員函式可取得定位器類型。  
  
```  
BOOL GetLocatorType(DWORD& dwRef) const;  
```  
  
### <a name="parameters"></a>參數  
 *dwRef*  
 若要參考`DWORD`，將會收到定位器類型。 請參閱**備註**定位器類型的資料表。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。 如果呼叫失敗，Win32 函式[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)可能會呼叫以判斷錯誤的原因。  
  
### <a name="remarks"></a>備註  
 可能的類型如下所示：  
  
|值|意義|  
|-----------|-------------|  
|GOPHER_TYPE_TEXT_FILE|ASCII 文字檔案。|  
|GOPHER_TYPE_DIRECTORY|其他 Gopher 項目的目錄。|  
|GOPHER_TYPE_CSO|CSO 電話簿伺服器。|  
|GOPHER_TYPE_ERROR|指出錯誤條件。|  
|GOPHER_TYPE_MAC_BINHEX|Macintosh 的 BINHEX 格式檔案。|  
|GOPHER_TYPE_DOS_ARCHIVE|DOS 封存檔。|  
|GOPHER_TYPE_UNIX_UUENCODED|Uuencode 編碼檔案。|  
|GOPHER_TYPE_INDEX_SERVER|索引伺服器。|  
|GOPHER_TYPE_TELNET|Telnet 伺服器。|  
|GOPHER_TYPE_BINARY|二進位檔案。|  
|GOPHER_TYPE_REDUNDANT|重複的伺服器。 中包含的資訊是主要伺服器的複本。 主要伺服器是最後一個沒有 GOPHER_TYPE_REDUNDANT 類型的目錄項目。|  
|GOPHER_TYPE_TN3270|TN3270 伺服器。|  
|GOPHER_TYPE_GIF|GIF 圖形檔。|  
|GOPHER_TYPE_IMAGE|映像檔案。|  
|GOPHER_TYPE_BITMAP|點陣圖檔案。|  
|GOPHER_TYPE_MOVIE|影片檔。|  
|GOPHER_TYPE_SOUND|音效檔。|  
|GOPHER_TYPE_HTML|HTML 文件。|  
|GOPHER_TYPE_PDF|此 PDF 檔案。|  
|GOPHER_TYPE_CALENDAR|行事曆檔案。|  
|GOPHER_TYPE_INLINE|內嵌檔。|  
|GOPHER_TYPE_UNKNOWN|未知的項目類型。|  
|GOPHER_TYPE_ASK|請洽詢 + 項目。|  
|GOPHER_TYPE_GOPHER_PLUS|Gopher + 項目。|  
  
##  <a name="operator_lpctstr"></a>  CGopherLocator::operator LPCTSTR  
 這很有用的轉型運算子提供有效率的方法來存取中包含 null 結束的 C 字串`CGopherLocator`物件。  
  
```  
operator LPCTSTR () const;  
```  
  
### <a name="return-value"></a>傳回值  
 字串資料的字元指標。  
  
### <a name="remarks"></a>備註  
 沒有字元會複製;只有指標會傳回。  
  
## <a name="see-also"></a>另請參閱  
 [CObject 類別](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CGopherFileFind 類別](../../mfc/reference/cgopherfilefind-class.md)
