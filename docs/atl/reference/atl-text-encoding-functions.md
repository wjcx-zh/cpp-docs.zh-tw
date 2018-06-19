---
title: ATL 文字編碼函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlGetHexValue
- atlbase/ATL::AtlGetVersion
- atlenc/ATL::AtlHexDecode
- atlenc/ATL::AtlHexDecodeGetRequiredLength
- atlenc/ATL::AtlHexEncode
- atlenc/ATL::AtlHexEncodeGetRequiredLength
- atlenc/ATL::AtlHexValue
- atlenc/ATL::BEncode
- atlenc/ATL::BEncodeGetRequiredLength
- atlenc/ATL::EscapeXML
- atlenc/ATL::GetExtendedChars
- atlenc/ATL::IsExtendedChar
- atlenc/ATL::QEncode
- atlenc/ATL::QEncodeGetRequiredLength
- atlenc/ATL::QPDecode
- atlenc/ATL::QPDecodeGetRequiredLength
- atlenc/ATL::QPEncode
- atlenc/ATL::QPEncodeGetRequiredLength
- atlenc/ATL::UUDecode
- atlenc/ATL::UUDecodeGetRequiredLength
- atlenc/ATL::UUEncode
- atlenc/ATL::UUEncodeGetRequiredLength
ms.assetid: 2ae1648b-2b87-4112-92aa-0069fcfd23da
ms.openlocfilehash: 26eb0709c4009070e6255c6ee178f19d13d8a9c3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32366074"
---
# <a name="atl-text-encoding-functions"></a>ATL 文字編碼函式
這些函式支援編碼和解碼的文字。

|||  
|-|-|  
|[AtlGetHexValue](#atlgethexvalue)|呼叫此函式可取得十六進位的數值。|   
|[AtlGetVersion](#atlgetversion)|呼叫此函式可取得您正在使用 ATL 程式庫的版本。  |  
|[AtlHexDecode](#atlhexdecode)|將已由先前呼叫這類的十六進位文字編碼的資料字串解碼， [AtlHexEncode](#atlhexencode)。|
|[AtlHexDecodeGetRequiredLength](#atlhexdecodegetrequiredlength)|呼叫此函式可取得以位元組為單位的緩衝區大小，該緩衝區大小可包含從指定長度的十六進位編碼字串解碼的資料。|
|[AtlHexEncode](#atlhexencode)|呼叫此函式可將一些資料編碼為十六進位文字字串。|
|[AtlHexEncodeGetRequiredLength](#atlhexencodegetrequiredlength)|呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。|
|[AtlHexValue](#atlhexvalue)|呼叫此函式可取得十六進位的數值。 |
|[AtlUnicodeToUTF8](#atlunicodetoutf8)|呼叫此函式可將 Unicode 字串轉換為 UTF-8。 |
|[BEncode](#bencode)|呼叫此函式可使用 "B" 編碼方式轉換部分資料。|
|[BEncodeGetRequiredLength](#bencodegetrequiredlength)|呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。|
|[EscapeXML](#escapexml)|呼叫此函式可將無法在 XML 中安全使用的字元轉換成安全的對等字元。|
|[GetExtendedChars](#getextendedchars)|呼叫此函式可取得字串中的擴充字元數目。|
|[IsExtendedChar](#isextendedchar)|呼叫此函式，了解所指字元是否為擴充字元 (小於 32、大於 126，而且不是定位字元、換行字元或歸位字元)|
|[QEncode](#qencode)|呼叫此函式可使用 "Q" 編碼方式轉換部分資料。  |
|[QEncodeGetRequiredLength](#qencodegetrequiredlength)|呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。|
|[QPDecode](#qpdecode)|將已編碼的加上引號的可列印格式，例如由先前呼叫的資料字串解碼， [QPEncode](#qpencode)。|
|[QPDecodeGetRequiredLength](#qpdecodegetrequiredlength)|呼叫此函式可取得以位元組為單位的緩衝區大小，該緩衝區大小可包含從指定長度的加上引號可列印編碼字串解碼的資料。|
|[QPEncode](#qpencode)|呼叫此函式可採用加上引號的可列印格式對一些資料進行編碼。|
|[QPEncodeGetRequiredLength](#qpencodegetrequiredlength)|呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。|
|[UUDecode](#uudecode)|將已使用 uuencode 編碼例如由先前呼叫的資料字串解碼， [UUEncode](#uuencode)。|
|[UUDecodeGetRequiredLength](#uudecodegetrequiredlength)|呼叫此函式可取得以位元組為單位的緩衝區大小，該緩衝區大小可包含從指定長度的 UUENCODE 編碼字串解碼的資料。|
|[UUEncode](#uuencode)|呼叫此函式可對一些資料進行 UUENCODE 編碼。 |
|[UUEncodeGetRequiredLength](#uuencodegetrequiredlength)|呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。|

## <a name="requirements"></a>需求  
 **標頭：** atlenc.h  
 
## <a name="atlgethexvalue"></a> AtlGetHexValue
呼叫此函式可取得十六進位的數值。  
  
```    
inline char AtlGetHexValue(char chIn) throw();  
```  
  
### <a name="parameters"></a>參數  
 `chIn`  
 十六進位字元 '0'-'9'、 'A'-'F' 或 'a'-'f'。  
  
### <a name="return-value"></a>傳回值  
 輸入字元的數字值解譯為十六進位數字。 例如，輸入 '0' 的傳回值為 0 和 'A' 的輸入傳回值為 10。 如果輸入的字元不是十六進位數字，此函式會傳回-1。  
  
## <a name="atlgetversion"></a> AtlGetVersion
呼叫此函式可取得您正在使用 ATL 程式庫的版本。  
  
```  
ATLAPI_(DWORD) AtlGetVersion(void* pReserved);  
```  
  
### <a name="parameters"></a>參數  
 `pReserved`  
 保留的指標。  
  
### <a name="return-value"></a>傳回值  
 傳回`DWORD`ATL 程式庫，在編譯或執行版本的整數值。  
  
## <a name="example"></a>範例  
 此函式應該呼叫，如下所示。  
  
 [!code-cpp[NVC_ATL_Utilities#95](../../atl/codesnippet/cpp/atl-text-encoding-functions_1.cpp)]  
  
### <a name="requirements"></a>需求  
 **標頭：** atlbase.h  

## <a name="atlhexdecode"></a> AtlHexDecode
將已由先前呼叫這類的十六進位文字編碼的資料字串解碼， [AtlHexEncode](#atlhexencode)。  
  
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
 中的字元長度`pSrcData`。  
  
 `pbDest`  
 呼叫端配置緩衝區，以接收已解碼的資料。  
  
 `pnDestLen`  
 變數，其中包含以位元組為單位的長度指標`pbDest`。 如果函式成功，則變數會收到寫入緩衝區的位元組數目。 如果函式失敗，變數會收到所需的長度，以位元組為單位的緩衝區。  
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**成功時， **FALSE**失敗。  
  
## <a name="atlhexdecodegetrequiredlength"></a> AtlHexDecodeGetRequiredLength
呼叫此函式可取得以位元組為單位的緩衝區大小，該緩衝區大小可包含從指定長度的十六進位編碼字串解碼的資料。  
  
```  
inline int AtlHexDecodeGetRequiredLength(int nSrcLen) throw();  
```  
  
### <a name="parameters"></a>參數  
 `nSrcLen`  
 編碼字串的字元數。  
  
### <a name="return-value"></a>傳回值  
 所需的緩衝區，無法保存已解碼的字串的位元組數目`nSrcLen`字元。  
  
## <a name="atlhexencode"></a> AtlHexEncode
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
 包含要編碼資料的緩衝區。  
  
 `nSrcLen`  
 要編碼的資料長度以位元組為單位。  
  
 `szDest`  
 呼叫端配置緩衝區接收編碼的資料。  
  
 `pnDestLen`  
 變數，其中包含以字元為單位的長度指標`szDest`。 如果函式成功，則變數會收到寫入緩衝區的字元數。 如果函式失敗，變數會收到所需的長度，以字元為單位的緩衝區。  
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**成功時， **FALSE**失敗。  
  
### <a name="remarks"></a>備註  
 來源資料的每個位元組會編碼為十六進位的 2 個字元。  
  
## <a name="atlhexencodegetrequiredlength"></a> AtlHexEncodeGetRequiredLength
呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。  
  
```  
inline int AtlHexEncodeGetRequiredLength(int nSrcLen) throw();  
```  
  
### <a name="parameters"></a>參數  
 `nSrcLen`  
 資料要編碼的位元組數目。  
  
### <a name="return-value"></a>傳回值  
 提供的緩衝區，無法容納編碼的資料所需字元數目`nSrcLen`位元組。  
  
## <a name="atlhexvalue"></a> AtlHexValue
呼叫此函式可取得十六進位的數值。  
  
```  
inline short AtlHexValue(char chIn) throw();  
```  
  
### <a name="parameters"></a>參數  
 `chIn`  
 十六進位字元 '0'-'9'、 'A'-'F' 或 'a'-'f'。  
  
### <a name="return-value"></a>傳回值  
 輸入字元的數字值解譯為十六進位數字。 例如，輸入 '0' 的傳回值為 0 和 'A' 的輸入傳回值為 10。 如果輸入的字元不是十六進位數字，此函式會傳回-1。  
  
## <a name="atlunicodetoutf8"></a> AtlUnicodeToUTF8
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
 呼叫端配置緩衝區，以接收已轉換的字串。  
  
 `nDest`  
 以位元組為單位的緩衝區長度。  
  
### <a name="return-value"></a>傳回值  
 傳回已轉換的字串的字元數目。  
  
### <a name="remarks"></a>備註  
 若要判斷所需的已轉換的字串緩衝區的大小，呼叫此函式傳遞 0`szDest`和`nDest`。  
  
## <a name="bencode"></a> BEncode  
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
 包含要編碼資料的緩衝區。  
  
 `nSrcLen`  
 要編碼的資料長度以位元組為單位。  
  
 `szDest`  
 呼叫端配置緩衝區接收編碼的資料。  
  
 `pnDestLen`  
 變數，其中包含以字元為單位的長度指標`szDest`。 如果函式成功，則變數會收到寫入緩衝區的字元數。 如果函式失敗，變數會收到所需的長度，以字元為單位的緩衝區。  
  
 `pszCharSet`  
 設定為使用轉換的字元。  
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**成功時， **FALSE**失敗。  
  
### <a name="remarks"></a>備註  
 "B"編碼配置述 RFC 2047 ([http://www.ietf.org/rfc/rfc2047.txt](http://www.ietf.org/rfc/rfc2047.txt))。  
  
## <a name="bencodegetrequiredlength"></a> BEncodeGetRequiredLength 
呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。  
  
```  
inline int BEncodeGetRequiredLength(int nSrcLen, int nCharsetLen) throw();  
```  
  
### <a name="parameters"></a>參數  
 `nSrcLen`  
 資料要編碼的位元組數目。  
  
 `nCharsetLen`  
 以字元為單位設定為使用來進行轉換的字元長度。  
  
### <a name="return-value"></a>傳回值  
 提供的緩衝區，無法容納編碼的資料所需字元數目`nSrcLen`位元組。  
  
### <a name="remarks"></a>備註  
 "B"編碼配置述 RFC 2047 ([http://www.ietf.org/rfc/rfc2047.txt](http://www.ietf.org/rfc/rfc2047.txt))。  
  
## <a name="escapexml"></a> EscapeXML
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
 以字元為單位的要轉換的字串長度。  
  
 *szEsc*  
 呼叫端配置緩衝區，以接收已轉換的字串。  
  
 *nDestLen*  
 呼叫端配置緩衝區的字元長度。  
  
 `dwFlags`  
 描述如何執行轉換所 ATL_ESC 旗標。 

- `ATL_ESC_FLAG_NONE` 預設行為。 引號標記和所有格符號不會轉換。
- `ATL_ESC_FLAG_ATTR` 標記和單引號括住轉換成`&quot;`和`&apos;`分別。


  
### <a name="return-value"></a>傳回值  
 以字元為單位的已轉換的字串長度。  
  
### <a name="remarks"></a>備註  
 此函式所執行的可能轉換為表所示：  
  
|原始程式檔|目的地|  
|------------|-----------------|  
|\<|&lt;|  
|>|&gt;|  
|&|&amp;|  
|'|&apos;|  
|"|&quot;|  
  
## <a name="getextendedchars"></a> GetExtendedChars
呼叫此函式可取得字串中的擴充字元數目。  
  
```  
inline int GetExtendedChars(LPCSTR szSrc, int nSrcLen) throw();  
```  
  
### <a name="parameters"></a>參數  
 `szSrc`  
 要分析的字串。  
  
 `nSrcLen`  
 在字元字串的長度。  
  
### <a name="return-value"></a>傳回值  
 傳回由字串內找到的擴充字元數目[IsExtendedChar](#isextendedchar)。  
  
## <a name="isextendedchar"></a> IsExtendedChar
呼叫此函式，了解所指字元是否為擴充字元 (小於 32、大於 126，而且不是定位字元、換行字元或歸位字元)  
  
```  
inline int IsExtendedChar(char ch) throw();  
```  
  
### <a name="parameters"></a>參數  
 *ch*  
 要測試的字元  
  
### <a name="return-value"></a>傳回值  
 **TRUE**擴充字元，如果**FALSE**否則。  
  
## <a name="qencode"></a> QEncode
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
 包含要編碼資料的緩衝區。  
  
 `nSrcLen`  
 要編碼的資料長度以位元組為單位。  
  
 `szDest`  
 呼叫端配置緩衝區接收編碼的資料。  
  
 `pnDestLen`  
 變數，其中包含以字元為單位的長度指標`szDest`。 如果函式成功，則變數會收到寫入緩衝區的字元數。 如果函式失敗，變數會收到所需的長度，以字元為單位的緩衝區。  
  
 `pszCharSet`  
 設定為使用轉換的字元。  
  
 *pnNumEncoded*  
 緩衝區的指標，此變數會在傳回時包含已轉換的 unsafe 字元數目。  
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**成功時， **FALSE**失敗。  
  
### <a name="remarks"></a>備註  
 "Q"編碼配置述 RFC 2047 ([http://www.ietf.org/rfc/rfc2047.txt](http://www.ietf.org/rfc/rfc2047.txt))。  
  
## <a name="qencodegetrequiredlength"></a> QEncodeGetRequiredLength 
呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。  
  
```  
inline int QEncodeGetRequiredLength(int nSrcLen, int nCharsetLen) throw();  
```  
  
### <a name="parameters"></a>參數  
 `nSrcLen`  
 資料要編碼的位元組數目。  
  
 `nCharsetLen`  
 以字元為單位設定為使用來進行轉換的字元長度。  
  
### <a name="return-value"></a>傳回值  
 提供的緩衝區，無法容納編碼的資料所需字元數目`nSrcLen`位元組。  
  
### <a name="remarks"></a>備註  
 "Q"編碼配置述 RFC 2047 ([http://www.ietf.org/rfc/rfc2047.txt](http://www.ietf.org/rfc/rfc2047.txt))。  
  
## <a name="qpdecode"></a> QPDecode
將已編碼的加上引號的可列印格式，例如由先前呼叫的資料字串解碼， [QPEncode](#qpencode)。  
  
```  
inline BOOL QPDecode(  
   BYTE* pbSrcData,  
   int nSrcLen,  
   LPSTR szDest,  
   int* pnDestLen,  
   DWORD dwFlags = 0) throw();  
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pbSrcData`  
 包含要解碼的資料的緩衝區。  
  
 [輸入] `nSrcLen`  
 以位元組為單位的長度`pbSrcData`。  
  
 [輸出] `szDest`  
 呼叫端配置緩衝區，以接收已解碼的資料。  
  
 [輸出] `pnDestLen`  
 變數，其中包含以位元組為單位的長度指標`szDest`。 如果函式成功，則變數會收到寫入緩衝區的位元組數目。 如果函式失敗，變數會收到所需的長度，以位元組為單位的緩衝區。  
  
 [輸入] `dwFlags`  
 描述如何執行轉換的旗標。 請參閱[ATLSMTP_QPENCODE 旗標](http://msdn.microsoft.com/library/6b15a3ab-8e57-49e4-8104-09b26ebb96c4)。  
  
### <a name="return-value"></a>傳回值  
 成功時傳回 `TRUE`，失敗時則傳回 `FALSE`。  
  
### <a name="remarks"></a>備註  
 加上引號的可列印編碼配置述 RFC 2045 ([http://www.ietf.org/rfc/rfc2045.txt](http://www.ietf.org/rfc/rfc2045.txt))。  
  
## <a name="qpdecodegetrequiredlength"></a> QPDecodeGetRequiredLength
呼叫此函式可取得以位元組為單位的緩衝區大小，該緩衝區大小可包含從指定長度的加上引號可列印編碼字串解碼的資料。  
  
```  
inline int QPDecodeGetRequiredLength(int nSrcLen) throw();  
```  
  
### <a name="parameters"></a>參數  
 `nSrcLen`  
 編碼字串的字元數。  
  
### <a name="return-value"></a>傳回值  
 所需的緩衝區，無法保存已解碼的字串的位元組數目`nSrcLen`字元。  
  
### <a name="remarks"></a>備註  
 加上引號的可列印編碼配置述 RFC 2045 ([http://www.ietf.org/rfc/rfc2045.txt](http://www.ietf.org/rfc/rfc2045.txt))。  
  
## <a name="qpencode"></a> QPEncode
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
 包含要編碼資料的緩衝區。  
  
 `nSrcLen`  
 要編碼的資料長度以位元組為單位。  
  
 `szDest`  
 呼叫端配置緩衝區接收編碼的資料。  
  
 `pnDestLen`  
 變數，其中包含以字元為單位的長度指標`szDest`。 如果函式成功，則變數會收到寫入緩衝區的字元數。 如果函式失敗，變數會收到所需的長度，以字元為單位的緩衝區。  
  
 `dwFlags`  
 描述如何執行轉換所 ATLSMTP_QPENCODE 旗標。 
- `ATLSMTP_QPENCODE_DOT` 如果一段會出現在一行的開頭，它是加入至輸出，以及編碼。
- `ATLSMTP_QPENCODE_TRAILING_SOFT` 將附加`=\r\n`編碼的字串。

加上引號的可列印編碼配置述[RFC 2045](http://www.ietf.org/rfc/rfc2045.txt)。
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**成功時， **FALSE**失敗。  
  
### <a name="remarks"></a>備註  
 加上引號的可列印編碼配置述 RFC 2045 ([http://www.ietf.org/rfc/rfc2045.txt](http://www.ietf.org/rfc/rfc2045.txt))。  
  
## <a name="qpencodegetrequiredlength"></a> QPEncodeGetRequiredLength
呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。  
  
```  
inline int QPEncodeGetRequiredLength(int nSrcLen) throw ();  
```  
  
### <a name="parameters"></a>參數  
 `nSrcLen`  
 資料要編碼的位元組數目。  
  
### <a name="return-value"></a>傳回值  
 提供的緩衝區，無法容納編碼的資料所需字元數目`nSrcLen`位元組。  
  
### <a name="remarks"></a>備註  
 加上引號的可列印編碼配置述 RFC 2045 ([http://www.ietf.org/rfc/rfc2045.txt](http://www.ietf.org/rfc/rfc2045.txt))。  
  
## <a name="uudecode"></a> UUDecode
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
 呼叫端配置緩衝區，以接收已解碼的資料。  
  
 `pnDestLen`  
 變數，其中包含以位元組為單位的長度指標`pbDest`。 如果函式成功，則變數會收到寫入緩衝區的位元組數目。 如果函式失敗，變數會收到所需的長度，以位元組為單位的緩衝區。  
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**成功時， **FALSE**失敗。  
  
### <a name="remarks"></a>備註  
 這個 uuencoding 實作遵循 POSIX P1003.2b/D11 規格。  
  
## <a name="uudecodegetrequiredlength"></a> UUDecodeGetRequiredLength
呼叫此函式可取得以位元組為單位的緩衝區大小，該緩衝區大小可包含從指定長度的 UUENCODE 編碼字串解碼的資料。  
  
```  
inline int UUDecodeGetRequiredLength(int nSrcLen) throw ();  
```  
  
### <a name="parameters"></a>參數  
 `nSrcLen`  
 編碼字串的字元數。  
  
### <a name="return-value"></a>傳回值  
 所需的緩衝區，無法保存已解碼的字串的位元組數目`nSrcLen`字元。  
  
### <a name="remarks"></a>備註  
 這個 uuencoding 實作遵循 POSIX P1003.2b/D11 規格。  
  
## <a name="uuencode"></a> UUEncode
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
 包含要編碼資料的緩衝區。  
  
 `nSrcLen`  
 要編碼的資料長度以位元組為單位。  
  
 `szDest`  
 呼叫端配置緩衝區接收編碼的資料。  
  
 `pnDestLen`  
 變數，其中包含以字元為單位的長度指標`szDest`。 如果函式成功，則變數會收到寫入緩衝區的字元數。 如果函式失敗，變數會收到所需的長度，以字元為單位的緩衝區。  
  
 *lpszFile*  
 要加入至標頭中指定 ATLSMTP_UUENCODE_HEADER 時檔案`dwFlags`。  
  
 `dwFlags`  
 控制此函式的行為的旗標。 
- `ATLSMTP_UUENCODE_HEADE` 標頭會進行編碼。
- `ATLSMTP_UUENCODE_END` 將編碼的結尾。
- `ATLSMTP_UUENCODE_DOT` 將執行資料載滿。  
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**成功時， **FALSE**失敗。  
  
### <a name="remarks"></a>備註  
 這個 uuencoding 實作遵循 POSIX P1003.2b/D11 規格。  
  
## <a name="uuencodegetrequiredlength"></a> UUEncodeGetRequiredLength
呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。  
  
```  
inline int UUEncodeGetRequiredLength(int nSrcLen) throw ();  
```  
  
### <a name="parameters"></a>參數  
 `nSrcLen`  
 資料要編碼的位元組數目。  
  
### <a name="return-value"></a>傳回值  
 提供的緩衝區，無法容納編碼的資料所需字元數目`nSrcLen`位元組。  
  
### <a name="remarks"></a>備註  
 這個 uuencoding 實作遵循 POSIX P1003.2b/D11 規格。  
  
### <a name="see-also"></a>另請參閱  
 [概念](../../atl/active-template-library-atl-concepts.md)   
 [ATL COM 桌面元件](../../atl/atl-com-desktop-components.md)   