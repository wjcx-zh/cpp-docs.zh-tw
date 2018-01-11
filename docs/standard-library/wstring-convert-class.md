---
title: "wstring_convert 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- wstring/stdext::cvt::wstring_convert
- locale/std::wstring_convert::byte_string
- locale/std::wstring_convert::wide_string
- locale/std::wstring_convert::state_type
- locale/std::wstring_convert::int_type
- locale/std::wstring_convert::from_bytes
- locale/std::wstring_convert::to_bytes
- locale/std::wstring_convert::converted
- locale/std::wstring_convert::state
dev_langs: C++
helpviewer_keywords:
- stdext::cvt [C++], wstring_convert
- std::wstring_convert [C++], byte_string
- std::wstring_convert [C++], wide_string
- std::wstring_convert [C++], state_type
- std::wstring_convert [C++], int_type
- std::wstring_convert [C++], from_bytes
- std::wstring_convert [C++], to_bytes
- std::wstring_convert [C++], converted
- std::wstring_convert [C++], state
ms.assetid: e34f5b65-d572-4bdc-ac69-20778712e376
caps.latest.revision: "25"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7753e2be6699bc789417d8afe9e9f49e55af7010
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="wstringconvert-class"></a>wstring_convert 類別
範本類別 `wstring_convert` 會執行寬字串與位元組字串之間的轉換。  
  
## <a name="syntax"></a>語法  
  
```
template <class Codecvt, class Elem = wchar_t>
class wstring_convert
```  
  
#### <a name="parameters"></a>參數  
 Codecvt  
 [locale](../standard-library/locale-class.md) Facet，代表轉換物件。  
  
 Elem  
 寬字元項目類型。  
  
## <a name="remarks"></a>備註  
 此範本類別會說明對類別 `std::basic_string<Elem>` 的寬字串物件與類別 `std::basic_string<char>` (也稱為 `std::string`) 的位元組字串物件之間的轉換進行控制的物件。 此範本類別會將類型 `wide_string` 和 `byte_string` 定義為這兩種類型的同義字。 `Elem` 值的序列 (儲存在 `wide_string` 物件中) 與多位元組序列 (儲存在 `byte_string` 物件中) 之間的轉換，是由類別 `Codecvt<Elem, char, std::mbstate_t>` 的物件所執行，其符合標準程式碼轉換 facet `std::codecvt<Elem, char, std::mbstate_t>` 的需求。  
  
 此樣板類別的物件會儲存：  
  
-   發生錯誤時顯示的位元組字串  
  
-   發生錯誤時顯示的寬字串  
  
-   配置的轉換物件的指標 (在終結 wbuffer_convert 物件時釋放)  
  
-   [state_type](#state_type) 類型的轉換狀態物件  
  
-   轉換計數  
  
### <a name="constructors"></a>建構函式  
  
|||  
|-|-|  
|[wstring_convert](#wstring_convert)|建構類型 `wstring_convert` 的物件。|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[byte_string](#byte_string)|代表位元組字串的類型。|  
|[wide_string](#wide_string)|代表寬字串的類型。|  
|[state_type](#state_type)|代表轉換狀態的類型。|  
|[int_type](#int_type)|代表整數的類型。|  
  
### <a name="member-functions"></a>成員函式  
  
|||  
|-|-|  
|[from_bytes](#from_bytes)|將位元組字串轉換為寬字串。|  
|[to_bytes](#to_bytes)|將寬字串轉換為位元組字串。|  
|[converted](#converted)|傳回成功轉換的數目。|  
|[state](#state)|傳回表示轉換狀態的物件。|  
  
## <a name="requirements"></a>需求  
 **標頭︰**\<locale>  
  
 **命名空間：** std  
  
##  <a name="byte_string"></a>  wstring_convert::byte_string  
 代表位元組字串的類型。  
  
```
typedef std::basic_string<char> byte_string;
```  
  
### <a name="remarks"></a>備註  
 此類型是 `std::basic_string<char>` 的同義字。  
  
##  <a name="converted"></a>  wstring_convert::converted  
 傳回成功轉換的數目。  
  
```
size_t converted() const;
```  
  
### <a name="return-value"></a>傳回值  
 成功轉換的數目。  
  
### <a name="remarks"></a>備註  
 成功轉換的數目會儲存在轉換計數物件中。  
  
##  <a name="from_bytes"></a>  wstring_convert::from_bytes  
 將位元組字串轉換為寬字串。  
  
```
wide_string from_bytes(char Byte);
wide_string from_bytes(const char* ptr);
wide_string from_bytes(const byte_string& Bstr);
wide_string from_bytes(const char* first, const char* last);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|`Byte`|要轉換的單一元素位元組序列。|  
|`ptr`|要轉換的 C-style、以 Null 結束的字元序列。|  
|`Bstr`|要轉換的 [byte_string](#byte_string)。|  
|`first`|在字元範圍中要轉換的第一個字元。|  
|`last`|在字元範圍中要轉換的最後一個字元。|  
  
### <a name="return-value"></a>傳回值  
 因轉換而產生的寬字串物件。  
  
### <a name="remarks"></a>備註  
 如果[轉換狀態](../standard-library/wstring-convert-class.md)物件 `not` 以明確的值來建構，則會在開始轉換前設定為其預設值 (初始的轉換狀態)。 否則會維持不變。  
  
 成功轉換的輸入項目數目會儲存在轉換計數物件中。 如果未發生轉換錯誤，成員函式會傳回已轉換的寬字串。 否則，如果物件是以 wide-string 錯誤訊息的初始設定式建構，則成員函式會傳回 wide-string 錯誤訊息物件。 否則，成員函式會擲回 [range_error](../standard-library/range-error-class.md) 類別的物件。  
  
##  <a name="int_type"></a>  wstring_convert::int_type  
 代表整數的類型。  
  
```
typedef typename wide_string::traits_type::int_type int_type;
```  
  
### <a name="remarks"></a>備註  
 此類型是 `wide_string::traits_type::int_type` 的同義字。  
  
##  <a name="state"></a>  wstring_convert::state  
 傳回表示轉換狀態的物件。  
  
```
state_type state() const;
```  
  
### <a name="return-value"></a>傳回值  
 [轉換狀態](../standard-library/wstring-convert-class.md)物件，代表轉換的狀態。  
  
### <a name="remarks"></a>備註  
  
##  <a name="state_type"></a>  wstring_convert::state_type  
 代表轉換狀態的類型。  
  
```
typedef typename Codecvt::state_type state_type;
```  
  
### <a name="remarks"></a>備註  
 此類型描述可代表轉換狀態的物件。 此類型是 `Codecvt::state_type` 的同義字。  
  
##  <a name="to_bytes"></a>  wstring_convert::to_bytes  
 將寬字串轉換為位元組字串。  
  
```
byte_string to_bytes(Elem Char);
byte_string to_bytes(const Elem* Wptr);
byte_string to_bytes(const wide_string& Wstr);
byte_string to_bytes(const Elem* first, const Elem* last);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|`Char`|要轉換的寬字元。|  
|`Wptr`|要轉換的 C-style、以 Null 結束的序列 (開始於 `wptr`)。|  
|`Wstr`|要轉換的 [wide_string](#wide_string)。|  
|`first`|項目範圍中要轉換的第一個項目。|  
|`last`|項目範圍中要轉換的最後一個項目。|  
  
### <a name="remarks"></a>備註  
 如果[轉換狀態](../standard-library/wstring-convert-class.md)物件 `not` 以明確的值來建構，則會在開始轉換前設定為其預設值 (初始的轉換狀態)。 否則會維持不變。  
  
 成功轉換的輸入項目數目會儲存在轉換計數物件中。 如果未發生轉換錯誤，成員函式會傳回已轉換的位元組字串。 否則，如果物件是以 byte-string 錯誤訊息的初始設定式建構，則成員函式會傳回 byte-string 錯誤訊息物件。 否則，成員函式會擲回 [range_error](../standard-library/range-error-class.md) 類別的物件。  
  
##  <a name="wide_string"></a>  wstring_convert::wide_string  
 代表寬字串的類型。  
  
```
typedef std::basic_string<Elem> wide_string;
```  
  
### <a name="remarks"></a>備註  
 此類型是 `std::basic_string<Elem>` 的同義字。  
  
##  <a name="wstring_convert"></a>  wstring_convert::wstring_convert  
 建構類型 `wstring_convert` 的物件。  
  
```
wstring_convert(Codecvt *Pcvt = new Codecvt);
wstring_convert(Codecvt *Pcvt, state_type _State);
wstring_convert(const byte_string& _Berr, const wide_string& Werr = wide_string());
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|`*Pcvt`|`Codecvt` 類型的物件，用以執行轉換。|  
|`_State`|[state_type](#state_type) 類型的物件，代表轉換狀態。|  
|`_Berr`|發生錯誤時顯示的 [byte_string](#byte_string)。|  
|`Werr`|發生錯誤時顯示的 [wide_string](#wide_string)。|  
  
### <a name="remarks"></a>備註  
 第一個建構函式會將 *Pcvt_arg* 儲存於[轉換物件](../standard-library/wstring-convert-class.md)中
