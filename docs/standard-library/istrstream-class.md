---
title: "istrstream 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- istrstream
- strstream/std::istrstream::rdbuf
- strstream/std::istrstream::str
dev_langs:
- C++
helpviewer_keywords:
- istrstream class
ms.assetid: c2d41c75-bd2c-4437-bd77-5939ce1b97af
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.openlocfilehash: 528634e98da7f57ee915124d38f20277495efcdb
ms.contentlocale: zh-tw
ms.lasthandoff: 04/29/2017

---
# <a name="istrstream-class"></a>istrstream 類別
描述一個物件，此物件可控制如何從 [strstreambuf](../standard-library/strstreambuf-class.md) 類別的資料流緩衝區中擷取元素和編碼物件。  
  
## <a name="syntax"></a>語法  
  
```
class istrstream : public istream
```  
  
## <a name="remarks"></a>備註  
 此物件會儲存類別 `strstreambuf` 的物件。  
  
> [!NOTE]
>  這個類別已被取代。 請考慮改用 [istringstream](../standard-library/sstream-typedefs.md#istringstream) 或 [wistringstream](../standard-library/sstream-typedefs.md#wistringstream)。  
  
### <a name="constructors"></a>建構函式  
  
|||  
|-|-|  
|[istrstream](#istrstream)|建構類型 `istrstream` 的物件。|  
  
### <a name="member-functions"></a>成員函式  
  
|||  
|-|-|  
|[rdbuf](#rdbuf)|將指標傳回至資料流的相關 `strstreambuf` 物件。|  
|[str](#str)|呼叫 [freeze](../standard-library/strstreambuf-class.md#freeze)，然後傳回指向受控制序列開頭的指標。|  
  
## <a name="requirements"></a>需求  
 **標頭：**\<strstream>  
  
 **命名空間：** std  
  
##  <a name="istrstream"></a>  istrstream::istrstream  
 建構類型 `istrstream` 的物件。  
  
```
explicit istrstream(
    const char* ptr);

explicit istrstream(
    char* ptr);

istrstream(
    const char* ptr,
    streamsize count);

istrstream(
    char* ptr,
    int count);
```  
  
### <a name="parameters"></a>參數  
 `count`  
 緩衝區 ( `ptr`) 的長度。  
  
 `ptr`  
 用來將緩衝區初始化的內容。  
  
### <a name="remarks"></a>備註  
 所有建構函式都會呼叫 [istream](../standard-library/istream-typedefs.md#istream)( **sb**) 來將基底類別初始化，其中 **sb** 是 [strstreambuf](../standard-library/strstreambuf-class.md) 類別的預存物件。 前兩個建構函式還會一併呼叫 `strstreambuf`( ( **const**`char` \*) `ptr`, 0 ) 來將 **sb** 初始化。 其餘兩個建構函式會改為呼叫 `strstreambuf`( ( **const**`char` *) `ptr`, `count` )。  
  
##  <a name="rdbuf"></a>  istrstream::rdbuf  
 傳回指向資料流相關 strstreambuf 物件的指標。  
  
```
strstreambuf *rdbuf() const
```  
  
### <a name="return-value"></a>傳回值  
 指向資料流相關 strstreambuf 物件的指標。  
  
### <a name="remarks"></a>備註  
 成員函式會傳回預存資料流緩衝區 (屬於 [strstreambuf](../standard-library/strstreambuf-class.md) 的 pointer 類型) 的位址。  
  
### <a name="example"></a>範例  
  如需使用 `rdbuf` 的範例，請參閱 [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount)。  
  
##  <a name="str"></a>  istrstream::str  
 呼叫 [freeze](../standard-library/strstreambuf-class.md#freeze)，然後傳回指向受控制序列開頭的指標。  
  
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
 [istream](../standard-library/istream-typedefs.md#istream)   
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 程式設計](../standard-library/iostream-programming.md)   
 [iostream 慣例](../standard-library/iostreams-conventions.md)




