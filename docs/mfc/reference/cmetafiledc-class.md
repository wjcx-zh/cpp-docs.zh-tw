---
title: "CMetaFileDC 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMetaFileDC
- AFXEXT/CMetaFileDC
- AFXEXT/CMetaFileDC::CMetaFileDC
- AFXEXT/CMetaFileDC::Close
- AFXEXT/CMetaFileDC::CloseEnhanced
- AFXEXT/CMetaFileDC::Create
- AFXEXT/CMetaFileDC::CreateEnhanced
dev_langs:
- C++
helpviewer_keywords:
- CMetaFileDC class
- Windows metafiles [C++]
- metafiles, implementing
ms.assetid: ffce60fa-4181-4d46-9832-25e46fad4db4
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
ms.openlocfilehash: 4bff4d7601c4ffbc6fe5cbe73f5e057b79abf1e5
ms.lasthandoff: 02/24/2017

---
# <a name="cmetafiledc-class"></a>CMetaFileDC 類別
實作 Windows 中繼檔，這個檔案包含一連串可重新執行來建立所需影像或文字的繪圖裝置介面 (GDI) 命令。  
  
## <a name="syntax"></a>語法  
  
```  
class CMetaFileDC : public CDC  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CMetaFileDC::CMetaFileDC](#cmetafiledc)|建構 `CMetaFileDC` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMetaFileDC::Close](#close)|關閉裝置內容，並建立中繼檔案控制代碼。|  
|[CMetaFileDC::CloseEnhanced](#closeenhanced)|關閉增強型中繼檔裝置內容，並建立增強型中繼檔控制代碼。|  
|[CMetaFileDC::Create](#create)|建立 Windows 中繼檔裝置內容，並將它附加`CMetaFileDC`物件。|  
|[CMetaFileDC::CreateEnhanced](#createenhanced)|建立格式增強型中繼檔的中繼檔裝置內容。|  
  
## <a name="remarks"></a>備註  
 若要實作 Windows 中繼檔，請先建立`CMetaFileDC`物件。 叫用`CMetaFileDC`建構函式，然後呼叫[建立](#create)成員函式，建立 Windows 中繼檔裝置內容，並將它附加`CMetaFileDC`物件。  
  
 接下來傳送`CMetaFileDC`物件的序列`CDC`GDI 命令您想要重新執行。 建立輸出，例如 GDI 命令`MoveTo`和`LineTo`，可以使用。  
  
 您所要的命令傳送至中繼檔之後，請呼叫**關閉**成員函式，會關閉中繼檔裝置內容，並傳回之中繼檔的控制代碼。 然後處置`CMetaFileDC`物件。  
  
 [CDC::PlayMetaFile](../../mfc/reference/cdc-class.md#playmetafile)然後可以使用中繼檔的控制代碼來重複播放中繼檔。 中繼檔也操作 Windows 函式由例如[CopyMetaFile](http://msdn.microsoft.com/library/windows/desktop/dd183480)，它將中繼檔複製到磁碟。  
  
 當不再需要的中繼檔時，它從記憶體中刪除與[DeleteMetaFile](http://msdn.microsoft.com/library/windows/desktop/dd183537) Windows 函式。  
  
 您也可以實作`CMetaFileDC`物件，使它可以處理兩者輸出呼叫，這類屬性 GDI 呼叫`GetTextExtent`。 這類中繼檔更有彈性，可以更輕鬆地重複使用一般 GDI 程式碼，其中通常包含混合的輸出和屬性呼叫。 `CMetaFileDC`類別會繼承兩種裝置內容，`m_hDC`和`m_hAttribDC`，從`CDC`。 `m_hDC`裝置內容會處理所有[CDC](../../mfc/reference/cdc-class.md) GDI 輸出呼叫和`m_hAttribDC`裝置內容會處理所有`CDC`GDI 屬性呼叫。 一般來說，在相同的裝置，請參閱以下兩種裝置內容。 如果是`CMetaFileDC`，DC 的屬性設為**NULL**預設。  
  
 建立指向螢幕、 印表機或裝置以外中繼檔，然後呼叫第二個裝置內容`SetAttribDC`成員函式來建立新的裝置內容與關聯`m_hAttribDC`。 資訊的 GDI 呼叫現在會導向至新`m_hAttribDC`。 輸出 GDI 呼叫將會移至`m_hDC`，用來表示中繼檔。  
  
 如需有關`CMetaFileDC`，請參閱[裝置內容](../../mfc/device-contexts.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDC](../../mfc/reference/cdc-class.md)  
  
 `CMetaFileDC`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxext.h  
  
##  <a name="close"></a>CMetaFileDC::Close  
 關閉中繼檔裝置內容，並建立可用來播放使用中繼檔的 Windows 中繼檔控制代碼[CDC::PlayMetaFile](../../mfc/reference/cdc-class.md#playmetafile)成員函式。  
  
```  
HMETAFILE Close();
```  
  
### <a name="return-value"></a>傳回值  
 有效**HMETAFILE**如果函式成功，否則**NULL**。  
  
### <a name="remarks"></a>備註  
 Windows 中繼檔處理常式也可用來操作與 Windows 函式的中繼檔，例如[CopyMetaFile](http://msdn.microsoft.com/library/windows/desktop/dd183480)。  
  
 在使用後刪除中繼檔，藉由呼叫 Windows [DeleteMetaFile](http://msdn.microsoft.com/library/windows/desktop/dd183537)函式。  
  
##  <a name="closeenhanced"></a>CMetaFileDC::CloseEnhanced  
 關閉增強型中繼檔裝置內容，並傳回識別格式增強型中繼檔的控制代碼。  
  
```  
HENHMETAFILE CloseEnhanced();
```  
  
### <a name="return-value"></a>傳回值  
 控制代碼的增強型中繼檔，如果登錄成功。否則**NULL**。  
  
### <a name="remarks"></a>備註  
 應用程式可以使用這個函式所傳回的增強型中繼檔控制代碼來執行下列工作︰  
  
-   顯示儲存在增強型中繼檔中的圖片  
  
-   建立複本的增強型中繼檔  
  
-   列舉、 編輯或複製個別記錄中增強型中繼檔  
  
-   增強型中繼檔標頭中擷取的中繼檔內容的選擇性描述  
  
-   擷取一份增強型中繼檔標頭  
  
-   擷取二進位增強型中繼檔的複本  
  
-   列舉中選擇性的調色盤色彩  
  
-   將格式增強型中繼檔轉換成 Windows 格式中繼檔  
  
 當應用程式不再需要的增強型中繼檔的控制代碼時，它應該釋放控制代碼藉由呼叫 Win32 **DeleteEnhMetaFile**函式。  
  
##  <a name="cmetafiledc"></a>CMetaFileDC::CMetaFileDC  
 建構`CMetaFileDC`兩個步驟中的物件。  
  
```  
CMetaFileDC();
```  
  
### <a name="remarks"></a>備註  
 首先，呼叫`CMetaFileDC`，然後呼叫**建立**，這會建立 Windows 中繼檔裝置內容，並將其以附加`CMetaFileDC`物件。  
  
##  <a name="create"></a>CMetaFileDC::Create  
 建構`CMetaFileDC`兩個步驟中的物件。  
  
```  
BOOL Create(LPCTSTR lpszFilename = NULL);
```  
  
### <a name="parameters"></a>參數  
 *lpszFilename*  
 指向以 null 結束的字元字串。 指定建立中繼檔的檔名。 如果*lpszFilename*是**NULL**，建立新的記憶體中中繼檔。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功則為非零，否則為 0。  
  
### <a name="remarks"></a>備註  
 首先，呼叫建構函式`CMetaFileDC`，然後呼叫**建立**，這會建立 Windows 中繼檔裝置內容，並將其以附加`CMetaFileDC`物件。  
  
##  <a name="createenhanced"></a>CMetaFileDC::CreateEnhanced  
 建立格式增強型中繼檔裝置內容。  
  
```  
BOOL CreateEnhanced(
    CDC* pDCRef,  
    LPCTSTR lpszFileName,  
    LPCRECT lpBounds,  
    LPCTSTR lpszDescription);
```  
  
### <a name="parameters"></a>參數  
 `pDCRef`  
 識別參考裝置的增強型中繼檔。  
  
 `lpszFileName`  
 指向以 null 結束的字元字串。 指定要建立的增強型中繼檔的檔案名稱。 如果這個參數是**NULL**，增強型中繼檔是記憶體為基礎或終結物件時遺失及其內容 Win32 **DeleteEnhMetaFile**函式呼叫。  
  
 `lpBounds`  
 指向[RECT](../../mfc/reference/rect-structure1.md)資料結構或[CRect](../../atl-mfc-shared/reference/crect-class.md)物件，指定在維度**HIMETRIC**單位 （伸.01 公釐） 的圖片儲存在增強型中繼檔。  
  
 `lpszDescription`  
 指向以零結尾的字串，指定建立應用程式的圖片，以及圖片的標題名稱。  
  
### <a name="return-value"></a>傳回值  
 增強型中繼檔，如果成功; 的裝置內容控制代碼否則**NULL**。  
  
### <a name="remarks"></a>備註  
 這個網域控制站可以用來儲存與裝置無關的圖片。  
  
 Windows 會使用由參考裝置`pDCRef`參數來錄製解析度和裝置的圖片最初出現的單位。 如果`pDCRef`參數是**NULL**，它會使用參考目前的顯示裝置。  
  
 左邊和最上層成員`RECT`指向資料結構`lpBounds`參數分別必須小於右邊緣和下的成員。 邊緣的矩形的點包含在圖片中。 如果`lpBounds`是**NULL**，繪圖裝置介面 (GDI) 會計算最小矩形，可以將圖片繪製應用程式的維度。 `lpBounds`應該提供參數，在可能的情況。  
  
 指向字串`lpszDescription`參數必須包含 null 字元的應用程式名稱和圖片名稱之間，且必須使用兩個 null 字元結束 — 例如，"XYZ 圖形 Editor\0Bald Eagle\0\0，"\0 代表 null 字元的位置。 如果`lpszDescription`是**NULL**，加強型中繼檔標頭中沒有對應項目。  
  
 應用程式會使用這個函式所建立的 DC，將圖形圖片儲存的增強型中繼檔。 識別此 DC 的控制代碼可以傳遞任何 GDI 函式。  
  
 應用程式中的增強型中繼檔會儲存圖片之後，它可以呼叫任何輸出裝置上顯示圖片`CDC::PlayMetaFile`函式。 顯示圖片，windows&2000; 會使用所指的矩形`lpBounds`參數和參考裝置來定位並調整圖片的解析度資料。 此函式所傳回的裝置內容會包含相同的預設屬性相關聯的任何新的 DC。  
  
 應用程式必須使用 Win32 **GetWinMetaFileBits**增強型中繼檔轉換成較舊的 Windows 中繼檔格式的函式。  
  
 應該使用增強型中繼檔的檔名。EMF 延伸模組。  
  
## <a name="see-also"></a>另請參閱  
 [CDC 類別](../../mfc/reference/cdc-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)




