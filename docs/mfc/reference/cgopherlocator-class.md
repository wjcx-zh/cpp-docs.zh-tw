---
title: CGopherLocator 類別 |Microsoft Docs
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
ms.openlocfilehash: aa231a2f232c6c834e05edfbca5d6023e0326d54
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43216732"
---
# <a name="cgopherlocator-class"></a>CGopherLocator 類別
從 gopher 伺服器取得 gopher 「 定位器 」，判斷定位器的類型，並將定位器提供給[CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)。  
  
> [!NOTE]
>  類別`CGopherConnection`， `CGopherFile`， `CGopherFileFind`，`CGopherLocator`和其成員已被取代，因為它們不在 Windows XP 平台上運作，但它們會繼續在舊版平台上運作。  
  
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
|[CGopherLocator::operator LPCTSTR](#operator_lpctstr)|直接存取儲存在字元`CGopherLocator`為 C 樣式字串的物件。|  
  
## <a name="remarks"></a>備註  
 應用程式必須取得 gopher 伺服器的定位器之前它可以擷取該伺服器中的資訊。 Jakmile obsahuje 定位器時，它必須視為不透明的語彙基元來定位程式。  
  
 每個 gopher 定位器已判斷的檔案或找到的伺服器類型的屬性。 請參閱[GetLocatorType](#getlocatortype) gopher 定位器類型的清單。  
  
 應用程式的呼叫通常使用定位器[CGopherFileFind::FindFile](../../mfc/reference/cgopherfilefind-class.md#findfile)擷取特定資訊。  
  
 若要進一步了解如何`CGopherLocator`運作方式與其他 MFC 網際網路類別，請參閱文章[網際網路程式設計 WinInet](../../mfc/win32-internet-extensions-wininet.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CGopherLocator`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxinet.h  
  
##  <a name="cgopherlocator"></a>  CGopherLocator::CGopherLocator  
 此成員函式呼叫來建立`CGopherLocator`物件。  
  
```  
CGopherLocator(const CGopherLocator& ref);
```  
  
### <a name="parameters"></a>參數  
 *ref*  
 常數的參考`CGopherLocator`物件。  
  
### <a name="remarks"></a>備註  
 您永遠不會建立`CGopherLocator`直接物件。 請改為呼叫[CGopherConnection::CreateLocator](../../mfc/reference/cgopherconnection-class.md#createlocator)建立並傳回的指標`CGopherLocator`物件。  
  
##  <a name="getlocatortype"></a>  CGopherLocator::GetLocatorType  
 呼叫此成員函式，以取得定位器類型。  
  
```  
BOOL GetLocatorType(DWORD& dwRef) const;  
```  
  
### <a name="parameters"></a>參數  
 *dwRef*  
 對一個 DWORD，將會收到定位器類型的參考。 請參閱**備註**定位器類型的資料表。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。 如果呼叫失敗，Win32 函式[GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)可能會呼叫以判斷錯誤的原因。  
  
### <a name="remarks"></a>備註  
 可能的類型如下所示：  
  
|值|意義|  
|-----------|-------------|  
|GOPHER_TYPE_TEXT_FILE|ASCII 文字檔。|  
|GOPHER_TYPE_DIRECTORY|Gopher 的其他項目目錄。|  
|GOPHER_TYPE_CSO|CSO 電話簿伺服器。|  
|GOPHER_TYPE_ERROR|表示錯誤狀況。|  
|GOPHER_TYPE_MAC_BINHEX|Macintosh 的 BINHEX 格式檔案。|  
|GOPHER_TYPE_DOS_ARCHIVE|DOS 封存檔。|  
|GOPHER_TYPE_UNIX_UUENCODED|使用 uuencode 編碼檔案。|  
|GOPHER_TYPE_INDEX_SERVER|索引伺服器。|  
|GOPHER_TYPE_TELNET|Telnet 伺服器。|  
|GOPHER_TYPE_BINARY|二進位檔案。|  
|GOPHER_TYPE_REDUNDANT|重複的伺服器。 內含的資訊是主要伺服器的複本。 主要伺服器是最後一個沒有 GOPHER_TYPE_REDUNDANT 類型的目錄項目。|  
|GOPHER_TYPE_TN3270|TN3270 伺服器。|  
|GOPHER_TYPE_GIF|GIF 圖形檔案。|  
|GOPHER_TYPE_IMAGE|影像檔。|  
|GOPHER_TYPE_BITMAP|點陣圖檔案。|  
|GOPHER_TYPE_MOVIE|影片檔。|  
|GOPHER_TYPE_SOUND|音效檔。|  
|GOPHER_TYPE_HTML|HTML 文件。|  
|GOPHER_TYPE_PDF|此 PDF 檔案。|  
|GOPHER_TYPE_CALENDAR|行事曆檔案。|  
|GOPHER_TYPE_INLINE|Inline 檔。|  
|GOPHER_TYPE_UNKNOWN|未知的項目類型。|  
|GOPHER_TYPE_ASK|Ask + 項目。|  
|GOPHER_TYPE_GOPHER_PLUS|Gopher + 項目。|  
  
##  <a name="operator_lpctstr"></a>  CGopherLocator::operator LPCTSTR  
 這個實用的轉型運算子提供有效率的方法，來存取中包含的 null 終止 C 字串`CGopherLocator`物件。  
  
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
