---
title: "strstream 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- strstream
- strstream/std::strstream::freeze
- strstream/std::strstream::pcount
- strstream/std::strstream::rdbuf
- strstream/std::strstream::str
dev_langs:
- C++
helpviewer_keywords:
- strstream class
ms.assetid: 63f3be31-9e36-42b1-9715-a474a5997e2a
caps.latest.revision: 21
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
ms.openlocfilehash: a1d7d7799e1338c72404f5bcdb9d06e9bac763e5
ms.contentlocale: zh-tw
ms.lasthandoff: 04/29/2017

---
# <a name="strstream-class"></a>strstream 類別
描述一個物件，該物件可控制如何使用類別 [strstreambuf](../standard-library/strstreambuf-class.md) 的資料流緩衝區來插入及擷取項目和編碼物件。  
  
## <a name="syntax"></a>語法  
  
```
class strstream : public iostream
```  
  
## <a name="remarks"></a>備註  
 此物件會儲存類別 `strstreambuf` 的物件。  
  
> [!NOTE]
>  這個類別已被取代。 請考慮改用 [stringstream](../standard-library/sstream-typedefs.md#stringstream) 或 [wstringstream](../standard-library/sstream-typedefs.md#wstringstream)。  
  
### <a name="constructors"></a>建構函式  
  
|||  
|-|-|  
|[strstream](#strstream)|建構類型 `strstream` 的物件。|  
  
### <a name="member-functions"></a>成員函式  
  
|||  
|-|-|  
|[freeze](#freeze)|導致資料流緩衝區無法在資料流緩衝區作業中使用。|  
|[pcount](#pcount)|傳回寫入至受控制序列的元素計數。|  
|[rdbuf](#rdbuf)|將指標傳回至資料流的相關 `strstreambuf` 物件。|  
|[str](#str)|呼叫 [freeze](../standard-library/strstreambuf-class.md#freeze)，然後傳回指向受控制序列開頭的指標。|  
  
## <a name="requirements"></a>需求  
 **標頭：**\<strstream>  
  
 **命名空間：** std  
  
##  <a name="freeze"></a>  strstream::freeze  
 導致資料流緩衝區無法在資料流緩衝區作業中使用。  
  
```
void freeze(bool _Freezeit = true);
```  
  
### <a name="parameters"></a>參數  
 `_Freezeit`  
 `bool`，指出您是否要凍結資料流。  
  
### <a name="remarks"></a>備註  
 成員函式會呼叫 [rdbuf](#rdbuf) -> [freeze](../standard-library/strstreambuf-class.md#freeze)(_ *Freezeit*)。  
  
### <a name="example"></a>範例  
  如需使用 **freeze** 的範例，請參閱 [strstreambuf::freeze](../standard-library/strstreambuf-class.md#freeze)。  
  
##  <a name="pcount"></a>  strstream::pcount  
 傳回寫入至受控制序列的元素計數。  
  
```
streamsize pcount() const;
```  
  
### <a name="return-value"></a>傳回值  
 寫入受控制序列的項目數。  
  
### <a name="remarks"></a>備註  
 成員函式會傳回 [rdbuf](#rdbuf) -> [pcount](../standard-library/strstreambuf-class.md#pcount)。  
  
### <a name="example"></a>範例  
  如需使用 pcount 的範例，請參閱 [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount)。  
  
##  <a name="rdbuf"></a>  strstream::rdbuf  
 將指標傳回至資料流的相關 strstreambuf 物件。  
  
```
strstreambuf *rdbuf() const
```  
  
### <a name="return-value"></a>傳回值  
 指向資料流相關 strstreambuf 物件的指標。  
  
### <a name="remarks"></a>備註  
 成員函式會將類型 **pointer** 的已儲存資料流緩衝區位址傳回 [strstreambuf](../standard-library/strstreambuf-class.md)。  
  
### <a name="example"></a>範例  
  如需使用 `rdbuf` 的範例，請參閱 [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount)。  
  
##  <a name="str"></a>  strstream::str  
 呼叫 [freeze](../standard-library/strstreambuf-class.md#freeze)，然後將指標傳回至受控制序列的開頭。  
  
```
char *str();
```  
  
### <a name="return-value"></a>傳回值  
 指向受控制序列開頭的指標。  
  
### <a name="remarks"></a>備註  
 成員函式會傳回 [rdbuf](#rdbuf) -> [str](../standard-library/strstreambuf-class.md#str)。  
  
### <a name="example"></a>範例  
  如需使用 **str** 的範例，請參閱 [strstreambuf::str](../standard-library/strstreambuf-class.md#str)。  
  
##  <a name="strstream"></a>  strstream::strstream  
 建構類型 `strstream` 的物件。  
  
```
strstream();

strstream(char* ptr,
    streamsize count,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```  
  
### <a name="parameters"></a>參數  
 `count`  
 緩衝區的大小。  
  
 `_Mode`  
 緩衝區的輸入和輸出模式。 如需詳細資訊，請參閱 [ios_base::openmode](../standard-library/ios-base-class.md#openmode)。  
  
 `ptr`  
 緩衝區。  
  
### <a name="remarks"></a>備註  
 這兩個建構函式會呼叫 [streambuf](../standard-library/streambuf-typedefs.md#streambuf)( **sb**) 來初始化基底類別，其中 **sb** 是類別 [strstreambuf](../standard-library/strstreambuf-class.md) 的已儲存物件。 第一個建構函式也會呼叫 [strstreambuf](../standard-library/strstreambuf-class.md#strstreambuf) 來初始化 **sb**。 第二個建構函式會使用下列其中一種方法來初始化基底類別：  
  
-   如果 `_Mode` & **ios_base::app**== 0，則 `ptr` 必須指定 `count` 項目陣列的第一個項目，且建構函式會呼叫 `strstreambuf`( `ptr`, `count`, `ptr`)。  
  
-   否則，`ptr` 必須指定 count 項目陣列 (包含 C 字串) 第一個項目，其第一個項目是由 `ptr` 指定，且建構函式會呼叫 `strstreambuf`( `ptr`, `count`, `ptr` + `strlen`( `ptr`) )。  
  
## <a name="see-also"></a>另請參閱  
 [iostream](../standard-library/istream-typedefs.md#iostream)   
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 程式設計](../standard-library/iostream-programming.md)   
 [iostream 慣例](../standard-library/iostreams-conventions.md)




