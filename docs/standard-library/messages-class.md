---
title: "messages 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- xlocmes/std::messages
- xlocmes/std::messages::char_type
- xlocmes/std::messages::string_type
- xlocmes/std::messages::close
- xlocmes/std::messages::do_close
- xlocmes/std::messages::do_get
- xlocmes/std::messages::do_open
- xlocmes/std::messages::get
- xlocmes/std::messages::open
dev_langs:
- C++
helpviewer_keywords:
- std::messages [C++]
- std::messages [C++], char_type
- std::messages [C++], string_type
- std::messages [C++], close
- std::messages [C++], do_close
- std::messages [C++], do_get
- std::messages [C++], do_open
- std::messages [C++], get
- std::messages [C++], open
ms.assetid: c4c71f40-4f24-48ab-9f7c-daccd8d5bd83
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 809a5fc0a74408c484948309a62096c2e89b7af5
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="messages-class"></a>messages 類別
此樣板類別描述可以做為地區設定 facet 的物件，以便從特定地區設定的國際化訊息目錄擷取當地語系化訊息。  
  
 目前，雖然實作 messages 類別，但沒有訊息。  
  
## <a name="syntax"></a>語法  
  
```
template <class CharType>  
class messages : public messages_base;
```  
  
#### <a name="parameters"></a>參數  
 `CharType`  
 程式內用於編碼地區設定字元的類型。  
  
## <a name="remarks"></a>備註  
 如同所有地區設定 facet，靜態物件識別碼有初始儲存值零。 第一次嘗試存取它的儲存值時，會在 **id** 中儲存一個唯一的正值。  
  
 這個 facet 基本上會開啟基底類別 messages_base 所定義的訊息目錄，擷取所需的資訊，並關閉目錄。  
  
### <a name="constructors"></a>建構函式  
  
|||  
|-|-|  
|[messages](#messages)|訊息 facet 建構函式。|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[char_type](#char_type)|用來顯示訊息的字元類型。|  
|[string_type](#string_type)|類型，描述包含 `basic_string` 類型字元的 `CharType` 類型字串。|  
  
### <a name="member-functions"></a>成員函式  
  
|||  
|-|-|  
|[close](#close)|關閉訊息目錄。|  
|[do_close](#do_close)|虛擬函式，呼叫以關閉訊息目錄。|  
|[do_get](#do_get)|虛擬函式，呼叫以擷取訊息目錄。|  
|[do_open](#do_open)|虛擬函式，呼叫以開啟訊息目錄。|  
|[get](#get)|擷取訊息目錄。|  
|[open](#open)|開啟訊息目錄。|  
  
## <a name="requirements"></a>需求  
 **標頭︰**\<locale>  
  
 **命名空間：** std  
  
##  <a name="char_type"></a>  messages::char_type  
 用來顯示訊息的字元類型。  
  
```
typedef CharType char_type;
```  
  
### <a name="remarks"></a>備註  
 此類型與樣板參數 **CharType** 同義。  
  
##  <a name="close"></a>  messages::close  
 關閉訊息目錄。  
  
```
void close(catalog _Catval) const;
```  
  
### <a name="parameters"></a>參數  
 `_Catval`  
 要關閉的目錄。  
  
### <a name="remarks"></a>備註  
 此成員函式會呼叫 [do_close](#do_close)(_ *Catval*)。  
  
##  <a name="do_close"></a>  messages::do_close  
 虛擬函式，呼叫以關閉訊息目錄。  
  
```
virtual void do_close(catalog _Catval) const;
```  
  
### <a name="parameters"></a>參數  
 `_Catval`  
 要關閉的目錄。  
  
### <a name="remarks"></a>備註  
 此受保護的成員函式會關閉訊息目錄 `_Catval`，這必須是透過先前對 [do_open](#do_open) 的呼叫來開啟的目錄。  
  
 *_Catval* 必須是從先前開啟且尚未關閉的目錄取得。  
  
### <a name="example"></a>範例  
  請參閱 [close](#close) 的範例，它會呼叫 `do_close`。  
  
##  <a name="do_get"></a>  messages::do_get  
 虛擬函式，呼叫以擷取訊息目錄。  
  
```
virtual string_type do_get(
    catalog _Catval,
    int _Set,
    int _Message,
    const string_type& _Dfault) const;
```  
  
### <a name="parameters"></a>參數  
 `_Catval`  
 識別值，指定所要搜尋的訊息目錄。  
  
 `_Set`  
 第一個識別的項目，用來找出訊息目錄中的訊息。  
  
 `_Message`  
 第二個識別的項目，用來找出訊息目錄中的訊息。  
  
 `_Dfault`  
 失敗時要傳回的字串。  
  
### <a name="return-value"></a>傳回值  
 它會在失敗時傳回 `_Dfault` 的複本。 否則，會傳回所指定訊息序列的複本。  
  
### <a name="remarks"></a>備註  
 此受保護的成員函式會嘗試從訊息目錄 `_Catval` 取得訊息序列。 這麼做時，它可能會利用 `_Set`、`_Message` 及 `_Dfault`。  
  
### <a name="example"></a>範例  
  請參閱 [get](#get) 的範例，它會呼叫 `do_get`。  
  
##  <a name="do_open"></a>  messages::do_open  
 虛擬函式，呼叫以開啟訊息目錄。  
  
```
virtual catalog do_open(
    const string& _Catname,
    const locale& _Loc) const;
```  
  
### <a name="parameters"></a>參數  
 `_Catname`  
 所要搜尋之目錄的名稱。  
  
 `_Loc`  
 要在目錄中搜尋的地區設定。  
  
### <a name="return-value"></a>傳回值  
 它會在失敗時傳回小於零的值。 否則，傳回的值可用來作為稍後對 [get](#get) 進行呼叫時的第一個引數。  
  
### <a name="remarks"></a>備註  
 此受保護的成員函式會嘗試開啟名稱為 `_Catname` 的訊息目錄。 這麼做時，它可能會利用地區設定 `_Loc`。  
  
 傳回值應該用來作為稍後對 [close](#close) 進行呼叫時的引數。  
  
### <a name="example"></a>範例  
  請參閱 [open](#open) 的範例，它會呼叫 `do_open`。  
  
##  <a name="get"></a>  messages::get  
 擷取訊息目錄。  
  
```
string_type get(
    catalog _CatVal,
    int _Set,
    int _Message,
    const string_type& _Dfault) const;
```  
  
### <a name="parameters"></a>參數  
 `_Catval`  
 識別值，指定所要搜尋的訊息目錄。  
  
 `_Set`  
 第一個識別的項目，用來找出訊息目錄中的訊息。  
  
 `_Message`  
 第二個識別的項目，用來找出訊息目錄中的訊息。  
  
 `_Dfault`  
 失敗時要傳回的字串。  
  
### <a name="return-value"></a>傳回值  
 它會在失敗時傳回 `_Dfault` 的複本。 否則，會傳回所指定訊息序列的複本。  
  
### <a name="remarks"></a>備註  
 此成員函式會傳回 [do_get](#do_get)( `_Catval`, `_Set`, `_Message`, `_Dfault`)。  
  
##  <a name="messages"></a>  messages::messages  
 訊息 facet 建構函式。  
  
```
explicit messages(
    size_t _Refs = 0);

protected: messages(
    const char* _Locname,
    size_t _Refs = 0);
```  
  
### <a name="parameters"></a>參數  
 `_Refs`  
 整數值，用來指定物件的記憶體管理類型。  
  
 `_Locname`  
 地區設定的名稱。  
  
### <a name="remarks"></a>備註  
 `_Refs` 參數的可能值和其意義如下：  
  
-   0：物件的存留期由包含該物件的地區設定來管理。  
  
-   1：物件的存留期必須以手動方式管理。  
  
-   \> 1： 未定義這些值。  
  
 無法提供任何直接範例，因為解構函式受到保護。  
  
 建構函式會以 **locale::**[facet](../standard-library/locale-class.md#facet_class)( `_Refs`) 將其基底物件初始化。  
  
##  <a name="open"></a>  messages::open  
 開啟訊息目錄。  
  
```
catalog open(
    const string& _Catname,
    const locale& _Loc) const;
```  
  
### <a name="parameters"></a>參數  
 `_Catname`  
 所要搜尋之目錄的名稱。  
  
 `_Loc`  
 要在目錄中搜尋的地區設定。  
  
### <a name="return-value"></a>傳回值  
 它會在失敗時傳回小於零的值。 否則，傳回的值可用來作為稍後對 [get](#get) 進行呼叫時的第一個引數。  
  
### <a name="remarks"></a>備註  
 此成員函式會傳回 [do_open](#do_open)( `_Catname`, `_Loc`)。  
  
##  <a name="string_type"></a>  messages::string_type  
 一種類型，描述包含 **CharType** 類型字元的 `basic_string` 類型字串。  
  
```
typedef basic_string<CharType, Traits, Allocator> string_type;
```  
  
### <a name="remarks"></a>備註  
 此類型描述 [basic_string](../standard-library/basic-string-class.md) 範本類別的特製化，其中此類別的物件可儲存訊息序列的複本。  
  
## <a name="see-also"></a>請參閱  
 [\<locale>](../standard-library/locale.md)   
 [messages_base 類別](../standard-library/messages-base-class.md)   
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)



