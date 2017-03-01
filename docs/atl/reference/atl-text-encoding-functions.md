---
title: "ATL 文字編碼函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ae1648b-2b87-4112-92aa-0069fcfd23da
caps.latest.revision: 3
translationtype: Machine Translation
ms.sourcegitcommit: 9ab4b38b2ba14aca2240d12fff966d36750a3229
ms.openlocfilehash: 86433bebe3fe84a027d7725525e028d80b67e358
ms.lasthandoff: 02/24/2017

---
# <a name="atl-text-encoding-functions"></a>ATL 文字編碼函式
這些函式支援編碼和解碼的文字。

|||  
|-|-|  
|[AtlGetHexValue](#atlgethexvalue)|呼叫此函式可取得十六進位的數值。|   
|[AtlGetVersion](#atlgetversion)|呼叫此函式可取得您正在使用 ATL 程式庫版本。  |  
|[AtlHexDecode](#atlhexdecode)|將已編碼為十六進位文字，例如由先前呼叫的資料字串解碼， [AtlHexEncode](#atlhexencode)。|
|[AtlHexDecodeGetRequiredLength](#atlhexdecodegetrequiredlength)|呼叫此函式可取得以位元組為單位的緩衝區大小，該緩衝區大小可包含從指定長度的十六進位編碼字串解碼的資料。|
|[AtlHexEncode](#atlhexencode)|呼叫此函式可將一些資料編碼為十六進位文字字串。|
|[AtlHexEncodeGetRequiredLength](#atlhexencodegetrequiredlength)|呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。|
|[AtlHexValue](#atlhexvalue)|呼叫此函式可取得十六進位的數值。 |
|[AtlUnicodeToUTF8](#atlunicodetoutf8)|呼叫此函式可將 Unicode 字串轉換為 UTF-8。 |
|[BEncode](#bencode)|呼叫此函式可使用 "B" 編碼方式轉換部分資料。|
|[BEncodeGetRequiredLength](#beencodegetrequiredlength)|呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。|
|[EscapeXML](#escapexml)|呼叫此函式可將無法在 XML 中安全使用的字元轉換成安全的對等字元。|
|[GetExtendedChars](#getextendedchars)|呼叫此函式可取得字串中的擴充字元數目。|
|[IsExtendedChar](#isextendedchar)|呼叫此函式，了解所指字元是否為擴充字元 (小於 32、大於 126，而且不是定位字元、換行字元或歸位字元)|
|[QEncode](#qencode)|呼叫此函式可使用 "Q" 編碼方式轉換部分資料。  |
|[QEncodeGetRequiredLength](#qencodegetrequiredlength)|呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。|
|[QPDecode](#qpdecode)|將具有已編碼，加上引號的可列印的格式，例如先前呼叫的資料字串解碼， [QPEncode](#qpencode)。|
|[QPDecodeGetRequiredLength](#qpdecodegetrequiredlength)|呼叫此函式可取得以位元組為單位的緩衝區大小，該緩衝區大小可包含從指定長度的加上引號可列印編碼字串解碼的資料。|
|[QPEncode](#qpencode)|呼叫此函式可採用加上引號的可列印格式對一些資料進行編碼。|
|[QPEncodeGetRequiredLength](#qpencodegetrequiredlength)|呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。|
|[UUDecode](#uudecode)|將已使用 uuencode 編碼例如由先前呼叫的資料字串解碼， [UUEncode](#uuencode)。|
|[UUDecodeGetRequiredLength](#uudecodegetrequiredlength)|呼叫此函式可取得以位元組為單位的緩衝區大小，該緩衝區大小可包含從指定長度的 UUENCODE 編碼字串解碼的資料。|
|[UUEncode](#uuencode)|呼叫此函式可對一些資料進行 UUENCODE 編碼。 |
|[UUEncodeGetRequiredLength](#uuencodegetrequiredlength)|呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。|

## <a name="requirements"></a>需求  
 **標頭︰** atlenc.h  
 
## <a name="a-nameatlgethexvaluea-atlgethexvalue"></a><a name="atlgethexvalue"></a>AtlGetHexValue
呼叫此函式可取得十六進位的數值。  
  
```    
inline char AtlGetHexValue(char chIn) throw();  
```  
  
### <a name="parameters"></a>參數  
 `chIn`  
 十六進位字元 '0'-'9'，'A'-'F'、 或 'a'-'f'。  
  
### <a name="return-value"></a>傳回值  
 輸入字元的數字值解譯為十六進位數字。 例如，'0' 的輸入傳回值為 0，而 'A' 的輸入傳回值為 10。 如果輸入的字元不是十六進位數字，此函式會傳回-1。  
  
## <a name="a-nameatlgetversiona-atlgetversion"></a><a name="atlgetversion"></a>AtlGetVersion
呼叫此函式可取得您正在使用 ATL 程式庫版本。  
  
```  
ATLAPI_(DWORD) AtlGetVersion(void* pReserved);  
```  
  
### <a name="parameters"></a>參數  
 `pReserved`  
 保留的指標。  
  
### <a name="return-value"></a>傳回值  
 傳回`DWORD`ATL 程式庫，在編譯或執行版本的整數值。  
  
## <a name="example"></a>範例  
 函式應該呼叫，如下所示。  
  
 [!code-cpp[NVC_ATL_Utilities #&95;](../../atl/codesnippet/cpp/atl-text-encoding-functions_1.cpp)]  
  
### <a name="requirements"></a>需求  
 **標頭︰** atlbase.h  

## <a name="a-nameatlhexdecodea-atlhexdecode"></a><a name="atlhexdecode"></a>AtlHexDecode
將已編碼為十六進位文字，例如由先前呼叫的資料字串解碼， [AtlHexEncode](#atlhexencode)。  
  
```    
inline BOOL AtlHexDecode(  
   LPCSTR pSrcData,  
   int nSrcLen,  
   LPBYTE pbDest,  
   int* pnDestLen) throw();  
```  
  
### <a name="parameters"></a>參數  
 `pSrcData`  
 字串，包含要解碼的資料。  
  
 `nSrcLen`  
 以字元為單位的長度`pSrcData`。  
  
 `pbDest`  
 呼叫端配置緩衝區以接收已解碼的資料。  
  
 `pnDestLen`  
 變數，其中包含以位元組為單位的長度指標`pbDest`。 如果函式成功，變數就會收到寫入緩衝區的位元組數目。 如果函式失敗，變數會接收所需的長度，以位元組為單位的緩衝區。  
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**成功時， **FALSE**失敗。  
  
## <a name="a-nameatlhexdecodegetrequiredlengtha-atlhexdecodegetrequiredlength"></a><a name="atlhexdecodegetrequiredlength"></a>AtlHexDecodeGetRequiredLength
呼叫此函式可取得以位元組為單位的緩衝區大小，該緩衝區大小可包含從指定長度的十六進位編碼字串解碼的資料。  
  
```  
inline int AtlHexDecodeGetRequiredLength(int nSrcLen) throw();  
```  
  
### <a name="parameters"></a>參數  
 `nSrcLen`  
 編碼的字串中的字元數。  
  
### <a name="return-value"></a>傳回值  
 無法保存已解碼的字串的緩衝區所需的位元組數目`nSrcLen`字元。  
  
## <a name="a-nameatlhexencodea-atlhexencode"></a><a name="atlhexencode"></a>AtlHexEncode
呼叫此函式可將一些資料編碼為十六進位文字字串。  
  
```  
inline BOOL AtlHexEncode(  
   const BYTE * pbSrcData,  
   int nSrcLen,  
   LPSTR szDest,  
int * pnDestLen) throw();  
```  
  
### <a name="parameters"></a>參數  
 `pbSrcData`  
 包含要編碼的資料緩衝區。  
  
 `nSrcLen`  
 要編碼的資料長度以位元組為單位。  
  
 `szDest`  
 呼叫端配置緩衝區接收編碼的資料。  
  
 `pnDestLen`  
 包含的字元長度的變數的指標`szDest`。 如果函式成功，變數就會收到寫入緩衝區的字元數。 如果函式失敗，變數會接收所需的長度，以字元為單位的緩衝區。  
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**成功時， **FALSE**失敗。  
  
### <a name="remarks"></a>備註  
 來源資料的每一個位元組會編碼為 2 個十六進位字元。  
  
## <a name="a-nameatlhexencodegetrequiredlengtha-atlhexencodegetrequiredlength"></a><a name="atlhexencodegetrequiredlength"></a>AtlHexEncodeGetRequiredLength
呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。  
  
```  
inline int AtlHexEncodeGetRequiredLength(int nSrcLen) throw();  
```  
  
### <a name="parameters"></a>參數  
 `nSrcLen`  
 要編碼的資料的位元組數目。  
  
### <a name="return-value"></a>傳回值  
 所需的緩衝區可以保留編碼的資料的字元數目`nSrcLen`位元組。  
  
## <a name="a-nameatlhexvaluea-atlhexvalue"></a><a name="atlhexvalue"></a>AtlHexValue
呼叫此函式可取得十六進位的數值。  
  
```  
inline short AtlHexValue(char chIn) throw();  
```  
  
### <a name="parameters"></a>參數  
 `chIn`  
 十六進位字元 '0'-'9'，'A'-'F'、 或 'a'-'f'。  
  
### <a name="return-value"></a>傳回值  
 輸入字元的數字值解譯為十六進位數字。 例如，'0' 的輸入傳回值為 0，而 'A' 的輸入傳回值為 10。 如果輸入的字元不是十六進位數字，此函式會傳回-1。  
  
## <a name="a-nameatlunicodetoutf8a-atlunicodetoutf8"></a><a name="atlunicodetoutf8"></a>AtlUnicodeToUTF8
呼叫此函式可將 Unicode 字串轉換為 UTF-8。  
  
```  
ATL_NOINLINE inline int AtlUnicodeToUTF8(  
   LPCWSTR wszSrc,  
   int nSrc,  
   LPSTR szDest,  
   int nDest) throw();  
```  
  
### <a name="parameters"></a>參數  
 *wszSrc*  
 要轉換的 Unicode 字串  
  
 `nSrc`  
 Unicode 字串的字元長度。  
  
 `szDest`  
 呼叫端配置緩衝區以接收已轉換的字串。  
  
 `nDest`  
 以位元組為單位的緩衝區長度。  
  
### <a name="return-value"></a>傳回值  
 傳回已轉換的字串的字元數目。  
  
### <a name="remarks"></a>備註  
 若要判斷所需的已轉換的字串緩衝區的大小，呼叫此函式，將 0 傳遞`szDest`和`nDest`。  
  
## <a name="a-namebencodea-bencode"></a><a name="bencode"></a>BEncode  
呼叫此函式可使用 "B" 編碼方式轉換部分資料。  
  
```  
inline BOOL BEncode(  
   BYTE* pbSrcData,  
   int nSrcLen,  
   LPSTR szDest,  
   int* pnDestLen,  
   LPCSTR pszCharSet) throw();  
```  
  
### <a name="parameters"></a>參數  
 `pbSrcData`  
 包含要編碼的資料緩衝區。  
  
 `nSrcLen`  
 要編碼的資料長度以位元組為單位。  
  
 `szDest`  
 呼叫端配置緩衝區接收編碼的資料。  
  
 `pnDestLen`  
 包含的字元長度的變數的指標`szDest`。 如果函式成功，變數就會收到寫入緩衝區的字元數。 如果函式失敗，變數會接收所需的長度，以字元為單位的緩衝區。  
  
 `pszCharSet`  
 設定為使用轉換的字元。  
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**成功時， **FALSE**失敗。  
  
### <a name="remarks"></a>備註  
 "B"編碼配置述 RFC 2047 ([http://www.ietf.org/rfc/rfc2047.txt](http://www.ietf.org/rfc/rfc2047.txt))。  
  
## <a name="a-namebeencodegetrequiredlengtha-bencodegetrequiredlength"></a><a name="beencodegetrequiredlength"></a>BEncodeGetRequiredLength 
呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。  
  
```  
inline int BEncodeGetRequiredLength(int nSrcLen, int nCharsetLen) throw();  
```  
  
### <a name="parameters"></a>參數  
 `nSrcLen`  
 要編碼的資料的位元組數目。  
  
 `nCharsetLen`  
 要轉換使用的字元集的字元長度。  
  
### <a name="return-value"></a>傳回值  
 所需的緩衝區可以保留編碼的資料的字元數目`nSrcLen`位元組。  
  
### <a name="remarks"></a>備註  
 "B"編碼配置述 RFC 2047 ([http://www.ietf.org/rfc/rfc2047.txt](http://www.ietf.org/rfc/rfc2047.txt))。  
  
## <a name="a-nameescapexmla-escapexml"></a><a name="escapexml"></a>EscapeXML
呼叫此函式可將無法在 XML 中安全使用的字元轉換成安全的對等字元。  
  
```  
inline int EscapeXML(  
   const wchar_t * szIn,  
   int nSrcLen,  
   wchar_t * szEsc,  
   int nDestLen,  
   DWORD dwFlags = ATL_ESC_FLAG_NONE) throw();  
```  
  
### <a name="parameters"></a>參數  
 `szIn`  
 要轉換的字串。  
  
 *nSrclen*  
 要轉換之字串的字元長度。  
  
 *szEsc*  
 呼叫端配置緩衝區以接收已轉換的字串。  
  
 *nDestLen*  
 呼叫端配置緩衝區的字元長度。  
  
 `dwFlags`  
 描述如何執行轉換的旗標。 請參閱[ATL_ESC 旗標](http://msdn.microsoft.com/library/daf3aa3c-7498-4d63-9fb6-e05b4815c2b8)。  
  
### <a name="return-value"></a>傳回值  
 在轉換後字串的字元長度。  
  
### <a name="remarks"></a>備註  
 此函式所執行的可能轉換是表所示︰  
  
|來源|目的地|  
|------------|-----------------|  
|\<|&lt;|  
|>|&gt;|  
|&|&amp;|  
|'|&apos;|  
|"|&quot;|  
  
## <a name="a-namegetextendedcharsa-getextendedchars"></a><a name="getextendedchars"></a>GetExtendedChars
呼叫此函式可取得字串中的擴充字元數目。  
  
```  
inline int GetExtendedChars(LPCSTR szSrc, int nSrcLen) throw();  
```  
  
### <a name="parameters"></a>參數  
 `szSrc`  
 要分析的字串。  
  
 `nSrcLen`  
 中字元的字串長度。  
  
### <a name="return-value"></a>傳回值  
 傳回由字串內找到的擴充字元數目[IsExtendedChar](#isextendedchar)。  
  
## <a name="a-nameisextendedchara-isextendedchar"></a><a name="isextendedchar"></a>IsExtendedChar
呼叫此函式，了解所指字元是否為擴充字元 (小於 32、大於 126，而且不是定位字元、換行字元或歸位字元)  
  
```  
inline int IsExtendedChar(char ch) throw();  
```  
  
### <a name="parameters"></a>參數  
 *ch*  
 要測試的字元  
  
### <a name="return-value"></a>傳回值  
 **TRUE**擴充字元時，如果**FALSE**否則。  
  
## <a name="a-nameqencodea-qencode"></a><a name="qencode"></a>QEncode
呼叫此函式可使用 "Q" 編碼方式轉換部分資料。  
  
```  
inline BOOL QEncode(  
   BYTE* pbSrcData,  
   int nSrcLen,  
   LPSTR szDest,  
   int* pnDestLen,  
   LPCSTR pszCharSet,  
   int* pnNumEncoded = NULL) throw();  
```  
  
### <a name="parameters"></a>參數  
 `pbSrcData`  
 包含要編碼的資料緩衝區。  
  
 `nSrcLen`  
 要編碼的資料長度以位元組為單位。  
  
 `szDest`  
 呼叫端配置緩衝區接收編碼的資料。  
  
 `pnDestLen`  
 包含的字元長度的變數的指標`szDest`。 如果函式成功，變數就會收到寫入緩衝區的字元數。 如果函式失敗，變數會接收所需的長度，以字元為單位的緩衝區。  
  
 `pszCharSet`  
 設定為使用轉換的字元。  
  
 *pnNumEncoded*  
 緩衝區的指標，此變數會在傳回時包含不安全必須轉換的字元數目。  
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**成功時， **FALSE**失敗。  
  
### <a name="remarks"></a>備註  
 RFC 2047 中描述的"Q"編碼配置 ([http://www.ietf.org/rfc/rfc2047.txt](http://www.ietf.org/rfc/rfc2047.txt))。  
  
## <a name="a-nameqencodegetrequiredlengtha-qencodegetrequiredlength"></a><a name="qencodegetrequiredlength"></a>QEncodeGetRequiredLength 
呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。  
  
```  
inline int QEncodeGetRequiredLength(int nSrcLen, int nCharsetLen) throw();  
```  
  
### <a name="parameters"></a>參數  
 `nSrcLen`  
 要編碼的資料的位元組數目。  
  
 `nCharsetLen`  
 要轉換使用的字元集的字元長度。  
  
### <a name="return-value"></a>傳回值  
 所需的緩衝區可以保留編碼的資料的字元數目`nSrcLen`位元組。  
  
### <a name="remarks"></a>備註  
 RFC 2047 中描述的"Q"編碼配置 ([http://www.ietf.org/rfc/rfc2047.txt](http://www.ietf.org/rfc/rfc2047.txt))。  
  
## <a name="a-nameqpdecodea-qpdecode"></a><a name="qpdecode"></a>QPDecode
將具有已編碼，加上引號的可列印的格式，例如先前呼叫的資料字串解碼， [QPEncode](#qpencode)。  
  
```  
inline BOOL QPDecode(  
   BYTE* pbSrcData,  
   int nSrcLen,  
   LPSTR szDest,  
   int* pnDestLen,  
   DWORD dwFlags = 0) throw();  
```  
  
### <a name="parameters"></a>參數  
 [in] `pbSrcData`  
 包含要解碼的資料緩衝區。  
  
 [in] `nSrcLen`  
 以位元組為單位的長度`pbSrcData`。  
  
 [輸出] `szDest`  
 呼叫端配置緩衝區以接收已解碼的資料。  
  
 [輸出] `pnDestLen`  
 變數，其中包含以位元組為單位的長度指標`szDest`。 如果函式成功，變數就會收到寫入緩衝區的位元組數目。 如果函式失敗，變數會接收所需的長度，以位元組為單位的緩衝區。  
  
 [in] `dwFlags`  
 描述如何執行轉換的旗標。 請參閱[ATLSMTP_QPENCODE 旗標](http://msdn.microsoft.com/library/6b15a3ab-8e57-49e4-8104-09b26ebb96c4)。  
  
### <a name="return-value"></a>傳回值  
 成功時傳回 `TRUE`，失敗時則傳回 `FALSE`。  
  
### <a name="remarks"></a>備註  
 加上引號的可列印編碼配置在 RFC 2045 內所述 ([http://www.ietf.org/rfc/rfc2045.txt](http://www.ietf.org/rfc/rfc2045.txt))。  
  
## <a name="a-nameqpdecodegetrequiredlengtha-qpdecodegetrequiredlength"></a><a name="qpdecodegetrequiredlength"></a>QPDecodeGetRequiredLength
呼叫此函式可取得以位元組為單位的緩衝區大小，該緩衝區大小可包含從指定長度的加上引號可列印編碼字串解碼的資料。  
  
```  
inline int QPDecodeGetRequiredLength(int nSrcLen) throw();  
```  
  
### <a name="parameters"></a>參數  
 `nSrcLen`  
 編碼的字串中的字元數。  
  
### <a name="return-value"></a>傳回值  
 無法保存已解碼的字串的緩衝區所需的位元組數目`nSrcLen`字元。  
  
### <a name="remarks"></a>備註  
 加上引號的可列印編碼配置在 RFC 2045 內所述 ([http://www.ietf.org/rfc/rfc2045.txt](http://www.ietf.org/rfc/rfc2045.txt))。  
  
## <a name="a-nameqpencodea-qpencode"></a><a name="qpencode"></a>QPEncode
呼叫此函式可採用加上引號的可列印格式對一些資料進行編碼。  
  
```  
inline BOOL QPEncode(  
   BYTE* pbSrcData,  
   int nSrcLen,  
   LPSTR szDest,  
   int* pnDestLen,  
   DWORD dwFlags = 0) throw ();  
```  
  
### <a name="parameters"></a>參數  
 `pbSrcData`  
 包含要編碼的資料緩衝區。  
  
 `nSrcLen`  
 要編碼的資料長度以位元組為單位。  
  
 `szDest`  
 呼叫端配置緩衝區接收編碼的資料。  
  
 `pnDestLen`  
 包含的字元長度的變數的指標`szDest`。 如果函式成功，變數就會收到寫入緩衝區的字元數。 如果函式失敗，變數會接收所需的長度，以字元為單位的緩衝區。  
  
 `dwFlags`  
 描述如何執行轉換的旗標。 請參閱[ATLSMTP_QPENCODE 旗標](http://msdn.microsoft.com/library/6b15a3ab-8e57-49e4-8104-09b26ebb96c4)。  
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**成功時， **FALSE**失敗。  
  
### <a name="remarks"></a>備註  
 加上引號的可列印編碼配置在 RFC 2045 內所述 ([http://www.ietf.org/rfc/rfc2045.txt](http://www.ietf.org/rfc/rfc2045.txt))。  
  
## <a name="a-nameqpencodegetrequiredlengtha-qpencodegetrequiredlength"></a><a name="qpencodegetrequiredlength"></a>QPEncodeGetRequiredLength
呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。  
  
```  
inline int QPEncodeGetRequiredLength(int nSrcLen) throw ();  
```  
  
### <a name="parameters"></a>參數  
 `nSrcLen`  
 要編碼的資料的位元組數目。  
  
### <a name="return-value"></a>傳回值  
 所需的緩衝區可以保留編碼的資料的字元數目`nSrcLen`位元組。  
  
### <a name="remarks"></a>備註  
 加上引號的可列印編碼配置在 RFC 2045 內所述 ([http://www.ietf.org/rfc/rfc2045.txt](http://www.ietf.org/rfc/rfc2045.txt))。  
  
## <a name="a-nameuudecodea-uudecode"></a><a name="uudecode"></a>UUDecode
將已使用 uuencode 編碼例如由先前呼叫的資料字串解碼， [UUEncode](#uuencode)。  
  
```  
inline BOOL UUDecode(  
   BYTE* pbSrcData,  
   int nSrcLen,  
   BYTE* pbDest,  
   int* pnDestLen) throw ();  
```  
  
### <a name="parameters"></a>參數  
 `pbSrcData`  
 字串，包含要解碼的資料。  
  
 `nSrcLen`  
 以位元組為單位的長度`pbSrcData`。  
  
 `pbDest`  
 呼叫端配置緩衝區以接收已解碼的資料。  
  
 `pnDestLen`  
 變數，其中包含以位元組為單位的長度指標`pbDest`。 如果函式成功，變數就會收到寫入緩衝區的位元組數目。 如果函式失敗，變數會接收所需的長度，以位元組為單位的緩衝區。  
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**成功時， **FALSE**失敗。  
  
### <a name="remarks"></a>備註  
 這個 uuencoding 實作遵循 POSIX P1003.2b/D11 規格。  
  
## <a name="a-nameuudecodegetrequiredlengtha-uudecodegetrequiredlength"></a><a name="uudecodegetrequiredlength"></a>UUDecodeGetRequiredLength
呼叫此函式可取得以位元組為單位的緩衝區大小，該緩衝區大小可包含從指定長度的 UUENCODE 編碼字串解碼的資料。  
  
```  
inline int UUDecodeGetRequiredLength(int nSrcLen) throw ();  
```  
  
### <a name="parameters"></a>參數  
 `nSrcLen`  
 編碼的字串中的字元數。  
  
### <a name="return-value"></a>傳回值  
 無法保存已解碼的字串的緩衝區所需的位元組數目`nSrcLen`字元。  
  
### <a name="remarks"></a>備註  
 這個 uuencoding 實作遵循 POSIX P1003.2b/D11 規格。  
  
## <a name="a-nameuuencodea-uuencode"></a><a name="uuencode"></a>UUEncode
呼叫此函式可對一些資料進行 UUENCODE 編碼。  
  
```  
inline BOOL UUEncode(  
   const BYTE* pbSrcData,  
   int nSrcLen,  
   LPSTR szDest,  
   int* pnDestLen,  
   LPCTSTR lpszFile = _T("file"),  
   DWORD dwFlags = 0) throw ();  
```  
  
### <a name="parameters"></a>參數  
 `pbSrcData`  
 包含要編碼的資料緩衝區。  
  
 `nSrcLen`  
 要編碼的資料長度以位元組為單位。  
  
 `szDest`  
 呼叫端配置緩衝區接收編碼的資料。  
  
 `pnDestLen`  
 包含的字元長度的變數的指標`szDest`。 如果函式成功，變數就會收到寫入緩衝區的字元數。 如果函式失敗，變數會接收所需的長度，以字元為單位的緩衝區。  
  
 *lpszFile*  
 要加入至標頭中指定 ATLSMTP_UUENCODE_HEADER 時檔案`dwFlags`。  
  
 `dwFlags`  
 控制這個函式行為的旗標。 請參閱[ATLSMTP_UUENCODE 旗標](http://msdn.microsoft.com/library/ecb79b81-b764-4a48-a05c-a9dee6e7bbce)。  
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**成功時， **FALSE**失敗。  
  
### <a name="remarks"></a>備註  
 這個 uuencoding 實作遵循 POSIX P1003.2b/D11 規格。  
  
## <a name="a-nameuuencodegetrequiredlengtha-uuencodegetrequiredlength"></a><a name="uuencodegetrequiredlength"></a>UUEncodeGetRequiredLength
呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。  
  
```  
inline int UUEncodeGetRequiredLength(int nSrcLen) throw ();  
```  
  
### <a name="parameters"></a>參數  
 `nSrcLen`  
 要編碼的資料的位元組數目。  
  
### <a name="return-value"></a>傳回值  
 所需的緩衝區可以保留編碼的資料的字元數目`nSrcLen`位元組。  
  
### <a name="remarks"></a>備註  
 這個 uuencoding 實作遵循 POSIX P1003.2b/D11 規格。  
  
### <a name="see-also"></a>另請參閱  
 [概念](../../atl/active-template-library-atl-concepts.md)   
 [ATL COM 桌面元件](../../atl/atl-com-desktop-components.md)   
