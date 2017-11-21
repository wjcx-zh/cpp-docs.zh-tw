---
title: "ostrstream 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- strstream/std::ostrstream::freeze
- strstream/std::ostrstream::pcount
- strstream/std::ostrstream::rdbuf
- strstream/std::ostrstream::str
dev_langs: C++
helpviewer_keywords:
- std::ostrstream [C++], freeze
- std::ostrstream [C++], pcount
- std::ostrstream [C++], rdbuf
- std::ostrstream [C++], str
ms.assetid: e2e34679-b266-4728-a8e1-8eda5d400e46
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 42b0786a140cf9657257d7f79a225a0473115282
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="ostrstream-class"></a>ostrstream 類別
描述一個物件，該物件可控制將項目和編碼物件插入 [strstreambuf](../standard-library/strstreambuf-class.md) 類別的資料流緩衝區中。  
  
## <a name="syntax"></a>語法  
  
```
class ostrstream : public ostream
```  
  
## <a name="remarks"></a>備註  
 此物件會儲存類別 `strstreambuf` 的物件。  
  
> [!NOTE]
>  這個類別已被取代。 請考慮改用 [ostringstream](../standard-library/sstream-typedefs.md#ostringstream) 或 [wostringstream](../standard-library/sstream-typedefs.md#wostringstream)。  
  
### <a name="constructors"></a>建構函式  
  
|||  
|-|-|  
|[ostrstream](#ostrstream)|建構類型 `ostrstream` 的物件。|  
  
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
  
##  <a name="freeze"></a>  ostrstream::freeze  
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
  如需使用 **freeze** 的範例，請參閱 [strstream::freeze](../standard-library/strstreambuf-class.md#freeze)。  
  
##  <a name="ostrstream"></a>  ostrstream::ostrstream  
 建構類型 `ostrstream` 的物件。  
  
```
ostrstream();

ostrstream(char* ptr,
    streamsize count,
    ios_base::openmode _Mode = ios_base::out);
```  
  
### <a name="parameters"></a>參數  
 `ptr`  
 緩衝區。  
  
 `count`  
 以位元組為單位的緩衝區大小。  
  
 `_Mode`  
 緩衝區的輸入和輸出模式。 如需詳細資訊，請參閱 [ios_base::openmode](../standard-library/ios-base-class.md#openmode)。  
  
### <a name="remarks"></a>備註  
 這兩個建構函式會呼叫 [ostream](../standard-library/ostream-typedefs.md#ostream)( **sb**) 來初始化基底類別，其中 **sb** 是類別 [strstreambuf](../standard-library/strstreambuf-class.md) 的已儲存物件。 第一個建構函式同時呼叫 `strstreambuf` 來初始化 **sb**。 第二個建構函式使用下列其中一種方法初始化基底類別：  
  
-   如果 `_Mode` & **ios_base::app**== 0，則 `ptr` 必須指定 `count` 項目陣列的第一個項目，且建構函式會呼叫 `strstreambuf`( `ptr`, `count`, `ptr`)。  
  
-   否則，`ptr` 必須指定 count 項目陣列 (包含 C 字串) 第一個項目，其第一個項目是由 `ptr` 指定，且建構函式會呼叫 `strstreambuf`( `ptr`, `count`, `ptr` + `strlen`( `ptr`) )。  
  
##  <a name="pcount"></a>  ostrstream::pcount  
 傳回寫入至受控制序列的元素計數。  
  
```
streamsize pcount() const;
```  
  
### <a name="return-value"></a>傳回值  
 寫入受控制序列的項目數。  
  
### <a name="remarks"></a>備註  
 成員函式會傳回 [rdbuf](#rdbuf) -> [pcount](../standard-library/strstreambuf-class.md#pcount)。  
  
### <a name="example"></a>範例  
  如需使用 `pcount` 的範例，請參閱 [strstream::pcount](../standard-library/strstreambuf-class.md#pcount)。  
  
##  <a name="rdbuf"></a>  ostrstream::rdbuf  
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
  
##  <a name="str"></a>  ostrstream::str  
 呼叫 [freeze](../standard-library/strstreambuf-class.md#freeze)，然後將指標傳回至受控制序列的開頭。  
  
```
char *str();
```  
  
### <a name="return-value"></a>傳回值  
 指向受控制序列開頭的指標。  
  
### <a name="remarks"></a>備註  
 成員函式會傳回 [rdbuf](#rdbuf) -> [str](../standard-library/strstreambuf-class.md#str)。  
  
### <a name="example"></a>範例  
  如需使用 **str** 的範例，請參閱 [strstream::str](../standard-library/strstreambuf-class.md#str)。  
  
## <a name="see-also"></a>另請參閱  
 [ostream](../standard-library/ostream-typedefs.md#ostream)   
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 程式設計](../standard-library/iostream-programming.md)   
 [iostream 慣例](../standard-library/iostreams-conventions.md)



