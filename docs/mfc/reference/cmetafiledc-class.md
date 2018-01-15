---
title: "CMetaFileDC 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
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
dev_langs: C++
helpviewer_keywords:
- CMetaFileDC [MFC], CMetaFileDC
- CMetaFileDC [MFC], Close
- CMetaFileDC [MFC], CloseEnhanced
- CMetaFileDC [MFC], Create
- CMetaFileDC [MFC], CreateEnhanced
ms.assetid: ffce60fa-4181-4d46-9832-25e46fad4db4
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8bb903bb38194be5b6a72f27ed683e965d7605b4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cmetafiledc-class"></a>CMetaFileDC 類別
實作 Windows 中繼檔，這個檔案包含一連串可重新執行來建立所需影像或文字的繪圖裝置介面 (GDI) 命令。  
  
## <a name="syntax"></a>語法  
  
```  
class CMetaFileDC : public CDC  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMetaFileDC::CMetaFileDC](#cmetafiledc)|建構 `CMetaFileDC` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMetaFileDC::Close](#close)|關閉裝置內容，並建立中繼檔的控制代碼。|  
|[CMetaFileDC::CloseEnhanced](#closeenhanced)|關閉增強型中繼檔裝置內容，並建立執行增強型中繼檔的控制代碼。|  
|[CMetaFileDC::Create](#create)|建立 Windows 中繼檔裝置內容，並將它附加至`CMetaFileDC`物件。|  
|[CMetaFileDC::CreateEnhanced](#createenhanced)|建立中繼檔裝置內容的格式增強型中繼檔。|  
  
## <a name="remarks"></a>備註  
 若要實作 Windows 中繼檔，請先建立`CMetaFileDC`物件。 叫用`CMetaFileDC`建構函式，然後呼叫[建立](#create)成員函式，以建立 Windows 中繼檔裝置內容，並將它附加至`CMetaFileDC`物件。  
  
 傳送給`CMetaFileDC`物件的順序`CDC`您想讓它重新執行的 GDI 命令。 建立輸出，例如 GDI 命令`MoveTo`和`LineTo`，可以使用。  
  
 您所需的命令傳送至中繼檔之後，請呼叫**關閉**成員函式，以關閉中繼檔裝置內容，並傳回的中繼檔的控制代碼。 然後處置`CMetaFileDC`物件。  
  
 [CDC::PlayMetaFile](../../mfc/reference/cdc-class.md#playmetafile)然後可以使用中繼檔的控制代碼來重複播放中繼檔。 中繼檔也操作 Windows 函式例如[CopyMetaFile](http://msdn.microsoft.com/library/windows/desktop/dd183480)，這會將中繼檔複製到磁碟。  
  
 當不再需要中繼檔時，它從記憶體中刪除與[DeleteMetaFile](http://msdn.microsoft.com/library/windows/desktop/dd183537) Windows 函式。  
  
 您也可以實作`CMetaFileDC`兩者輸出呼叫，例如屬性 GDI 呼叫物件，讓它可以處理`GetTextExtent`。 這類中繼檔更具彈性且可以更輕鬆地重複使用一般的 GDI 程式碼，其中通常包含混合的輸出和屬性的呼叫。 `CMetaFileDC`類別會繼承兩種裝置內容，`m_hDC`和`m_hAttribDC`，從`CDC`。 `m_hDC`裝置內容會處理所有[CDC](../../mfc/reference/cdc-class.md) GDI 輸出呼叫和`m_hAttribDC`裝置內容會處理所有`CDC`GDI 屬性呼叫。 一般來說，這些兩個裝置內容參考到相同的裝置。 如果是`CMetaFileDC`，DC 的屬性設為**NULL**預設。  
  
 建立指向螢幕、 印表機或裝置以外中繼檔，然後呼叫第二個裝置內容`SetAttribDC`成員函式來建立新的裝置內容與關聯`m_hAttribDC`。 資訊的 GDI 呼叫現在將會被導向至新`m_hAttribDC`。 輸出 GDI 呼叫將會移至`m_hDC`，用來表示中繼檔。  
  
 如需有關`CMetaFileDC`，請參閱[裝置內容](../../mfc/device-contexts.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDC](../../mfc/reference/cdc-class.md)  
  
 `CMetaFileDC`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxext.h  
  
##  <a name="close"></a>CMetaFileDC::Close  
 關閉中繼檔裝置內容，並建立可用來播放中繼檔使用的 Windows 中繼檔控制代碼[CDC::PlayMetaFile](../../mfc/reference/cdc-class.md#playmetafile)成員函式。  
  
```  
HMETAFILE Close();
```  
  
### <a name="return-value"></a>傳回值  
 有效**HMETAFILE**如果函式成功，否則**NULL**。  
  
### <a name="remarks"></a>備註  
 Windows 中繼檔處理常式也可用來操作 Windows 函式與中繼檔，例如[CopyMetaFile](http://msdn.microsoft.com/library/windows/desktop/dd183480)。  
  
 在使用後刪除中繼檔，藉由呼叫 Windows [DeleteMetaFile](http://msdn.microsoft.com/library/windows/desktop/dd183537)函式。  
  
##  <a name="closeenhanced"></a>CMetaFileDC::CloseEnhanced  
 關閉增強型中繼檔裝置內容，並傳回識別格式增強型中繼檔的控制代碼。  
  
```  
HENHMETAFILE CloseEnhanced();
```  
  
### <a name="return-value"></a>傳回值  
 控制代碼的增強型中繼檔，如果登錄成功。否則**NULL**。  
  
### <a name="remarks"></a>備註  
 應用程式可以使用這個函式所傳回的增強型中繼檔控制代碼來執行下列工作：  
  
-   顯示儲存在加強型中繼檔中的圖片  
  
-   建立複本的增強型中繼檔  
  
-   列舉、 編輯或複製個別記錄中的增強型中繼檔  
  
-   增強型中繼檔標頭中擷取的中繼檔內容的選擇性描述  
  
-   擷取一份增強型中繼檔標頭  
  
-   擷取二進位的增強型中繼檔複本  
  
-   列舉中的選擇性調色盤的色彩  
  
-   將轉換成 Windows 格式中繼檔的格式增強型中繼檔  
  
 當應用程式不再需要的增強型中繼檔的控制代碼時，它應該釋放控制代碼藉由呼叫 Win32 **DeleteEnhMetaFile**函式。  
  
##  <a name="cmetafiledc"></a>CMetaFileDC::CMetaFileDC  
 建構`CMetaFileDC`兩個步驟中的物件。  
  
```  
CMetaFileDC();
```  
  
### <a name="remarks"></a>備註  
 首先，呼叫`CMetaFileDC`，然後呼叫**建立**，建立 Windows 中繼檔裝置內容，並將它附加至`CMetaFileDC`物件。  
  
##  <a name="create"></a>CMetaFileDC::Create  
 建構`CMetaFileDC`兩個步驟中的物件。  
  
```  
BOOL Create(LPCTSTR lpszFilename = NULL);
```  
  
### <a name="parameters"></a>參數  
 *lpszFilename*  
 指向以 null 結尾字元字串。 指定建立中繼檔的檔名。 如果*lpszFilename*是**NULL**，建立新的記憶體中中繼檔。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功則為非零，否則為 0。  
  
### <a name="remarks"></a>備註  
 首先，呼叫建構函式`CMetaFileDC`，然後呼叫**建立**，建立 Windows 中繼檔裝置內容，並將它附加至`CMetaFileDC`物件。  
  
##  <a name="createenhanced"></a>CMetaFileDC::CreateEnhanced  
 建立裝置內容的格式增強型中繼檔。  
  
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
 指向以 null 結尾字元字串。 指定要建立的增強型中繼檔的檔案名稱。 如果這個參數是**NULL**，增強型中繼檔是記憶體為主的遺失或時終結物件及其內容 Win32 **DeleteEnhMetaFile**呼叫函式。  
  
 `lpBounds`  
 指向[RECT](../../mfc/reference/rect-structure1.md)資料結構或[CRect](../../atl-mfc-shared/reference/crect-class.md)物件，指定中的維度**HIMETRIC**單位 （.01 公釐為增量單位） 的圖片儲存在增強型中繼檔。  
  
 `lpszDescription`  
 指向以零結尾的字串，指定建立應用程式的圖片，以及圖片的標題名稱。  
  
### <a name="return-value"></a>傳回值  
 增強型中繼檔，如果成功; 的裝置內容控制代碼否則**NULL**。  
  
### <a name="remarks"></a>備註  
 此 DC 可以用來儲存與裝置無關的圖片。  
  
 Windows 會使用所識別的參考裝置`pDCRef`參數，以記錄的解決方式和裝置的圖片原本出現的單位。 如果`pDCRef`參數是**NULL**，它會使用目前的顯示裝置的參考。  
  
 左端和頂端成員`RECT`資料結構所指`lpBounds`參數分別必須小於右邊緣和下的成員。 矩形的邊緣點包含在圖片中。 如果`lpBounds`是**NULL**，圖形裝置介面 (GDI) 會計算最小矩形，可以將包含應用程式所繪製的圖片的維度。 `lpBounds`應該盡可能提供參數。  
  
 所指向之字串`lpszDescription`參數必須包含 null 字元的應用程式名稱與圖片名稱之間，且必須使用兩個 null 字元結束 — 例如，"XYZ 圖形 Editor\0Bald Eagle\0\0，"其中 \0 代表 null字元。 如果`lpszDescription`是**NULL**，增強型中繼檔標頭中沒有任何對應的項目。  
  
 應用程式會使用這個函式所建立的 DC，將圖形圖片儲存的增強型中繼檔。 識別此 DC 的控制代碼可以傳遞任何 GDI 函式。  
  
 應用程式的增強型中繼檔中所儲存圖片之後，它可以藉由呼叫任何輸出裝置上顯示圖片`CDC::PlayMetaFile`函式。 當顯示圖片時，Windows 會使用所指向的矩形`lpBounds`參數和參考裝置定位和調整圖片的解析度資料。 此函數所傳回的裝置內容，其中包含相關聯的任何新的 DC 相同的預設屬性。  
  
 應用程式必須使用 Win32 **GetWinMetaFileBits**較舊的 Windows 中繼檔格式轉換成增強型中繼檔的函式。  
  
 應該使用增強型中繼檔的檔名。EMF 延伸模組。  
  
## <a name="see-also"></a>請參閱  
 [CDC 類別](../../mfc/reference/cdc-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)



