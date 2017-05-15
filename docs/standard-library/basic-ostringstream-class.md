---
title: "basic_ostringstream 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- basic_ostringstream
- sstream/std::basic_ostringstream
- sstream/std::basic_ostringstream::allocator_type
- sstream/std::basic_ostringstream::rdbuf
- sstream/std::basic_ostringstream::str
dev_langs:
- C++
helpviewer_keywords:
- basic_ostringstream class
ms.assetid: aea699f7-350f-432a-acca-adbae7b483fb
caps.latest.revision: 19
author: corob-msft
ms.author: corob
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 96a5b0b6620810a336240e1adf06529c87bcb1b3
ms.contentlocale: zh-tw
ms.lasthandoff: 04/29/2017

---
# <a name="basicostringstream-class"></a>basic_ostringstream 類別
描述一個物件，該物件可控制如何將元素和編碼物件插入 [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`> 類別的資料流緩衝區。  
  
## <a name="syntax"></a>語法  
  
```  
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>  
class basic_ostringstream : public basic_ostream<Elem, Tr>  
```  
  
#### <a name="parameters"></a>參數  
 `Alloc`  
 配置器類別。  
  
 `Elem`  
 字串之基本項目的類型。  
  
 *Tr*  
 字元特性是在字串的基本項目上特製化。  
  
## <a name="remarks"></a>備註  
 此類別描述一個物件，該物件可控制如何將元素和編碼物件插入具有 **Elem** 類型之元素的資料流緩衝區；其中該類型的字元特性是由 **Tr** 類別所決定，而其元素是由 `Alloc` 類別的配置器所配置。 這個物件會儲存 basic_stringbuf< **Elem**, **Tr**, `Alloc`> 類別的物件。  
  
### <a name="constructors"></a>建構函式  
  
|||  
|-|-|  
|[basic_ostringstream](#basic_ostringstream)|建構類型 `basic_ostringstream` 的物件。|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[allocator_type](#allocator_type)|此類型是範本參數 `Alloc`的同義字。|  
  
### <a name="member-functions"></a>成員函式  
  
|||  
|-|-|  
|[rdbuf](#rdbuf)|將 `pointer` 類型之預存資料流緩衝區的位址傳回至 [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`, `Alloc`>。|  
|[str](#str)|設定或取得字串緩衝區中的文字，而不需要變更寫入位置。|  
  
## <a name="requirements"></a>需求  
 **標頭︰**\<sstream>  
  
 **命名空間：** std  
  
##  <a name="allocator_type"></a>  basic_ostringstream::allocator_type  
 此類型是範本參數 `Alloc`的同義字。  
  
```  
typedef Alloc allocator_type;  
```  
  
##  <a name="basic_ostringstream"></a>  basic_ostringstream::basic_ostringstream  
 建構 basic_ostringstream 類型的物件。  
  
```  
explicit basic_ostringstream(ios_base::openmode _Mode = ios_base::out);

explicit basic_ostringstream(const basic_string<Elem, Tr, Alloc>& str, ios_base::openmode _Mode = ios_base::out);
```  
  
### <a name="parameters"></a>參數  
 `_Mode`  
 [ios_base::openmode](../standard-library/ios-base-class.md#openmode) 中的其中一個列舉。  
  
 `str`  
 `basic_string` 類型的物件。  
  
### <a name="remarks"></a>備註  
 第一個建構函式會藉由呼叫 [basic_ostream](../standard-library/basic-ostream-class.md)( **sb**) 初始化基底類別，其中 **sb** 是 [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`> 類別的預存物件。 它也會藉由呼叫 basic_stringbuf< **Elem**, **Tr**, `Alloc`>( `_Mode` &#124; `ios_base::out`) 初始化 **sb**。  
  
 第二個建構函式會藉由呼叫 basic_ostream( **sb**) 初始化基底類別。 它也會藉由呼叫 basic_stringbuf< **Elem**, **Tr**, `Alloc`>(_ *Str*, `_Mode` &#124; `ios_base::out`) 初始化 **sb**。  
  
##  <a name="rdbuf"></a>  basic_ostringstream::rdbuf  
 將 **pointer** 類型之預存資料流緩衝區的位址傳回至 [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>。  
  
```  
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```  
  
### <a name="return-value"></a>傳回值  
 basic_stringbuf< **Elem**, **Tr**, `Alloc`> 的 **pointer** 類型之預存資料流緩衝區的位址。  
  
### <a name="remarks"></a>備註  
 此成員函式會將 **pointer** 類型之預存資料流緩衝區的位址傳回至 basic_stringbuf< **Elem**, **Tr**, `Alloc`>。  
  
### <a name="example"></a>範例  
  如需使用 `rdbuf` 的範例，請參閱 [basic_filebuf:: close](../standard-library/basic-filebuf-class.md#close)。  
  
##  <a name="str"></a>  basic_ostringstream::str  
 設定或取得字串緩衝區中的文字，而不需要變更寫入位置。  
  
```  
basic_string<Elem, Tr, Alloc> str() const;

 
void str(
    const basic_string<Elem, Tr, Alloc>& _Newstr);
```  
  
### <a name="parameters"></a>參數  
 `_Newstr`  
 新字串。  
  
### <a name="return-value"></a>傳回值  
 傳回 [basic_string](../standard-library/basic-string-class.md)< **Elem**, **Tr**, `Alloc`> 類別的物件，其受控制的序列是由 **\*this** 所控制的序列複本。  
  
### <a name="remarks"></a>備註  
 第一個成員函式會傳回 [rdbuf](#rdbuf) -> [str](../standard-library/basic-stringbuf-class.md#str)。 第二個成員函式會呼叫 `rdbuf` -> **str**( `_Newstr`)。  
  
### <a name="example"></a>範例  
  如需使用 **str** 的範例，請參閱 [basic_stringbuf:: str](../standard-library/basic-stringbuf-class.md#str)。  
  
## <a name="see-also"></a>另請參閱  
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 程式設計](../standard-library/iostream-programming.md)   
 [iostream 慣例](../standard-library/iostreams-conventions.md)


