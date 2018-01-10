---
title: "basic_iostream 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- istream/std::basic_iostream
- istream/std::basic_iostream::swap
dev_langs: C++
helpviewer_keywords: basic_iostream class
ms.assetid: 294b680b-eb49-4066-8db2-6d52dac9d6e3
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d415afefbde1f3903450a7c5e9f8f14e5cb78a7f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="basiciostream-class"></a>basic_iostream 類別
可執行輸入和輸出的資料流類別。  
  
## <a name="syntax"></a>語法  
  
```  
template <class Elem, class Tr = char_traits<Elem>>  
class basic_iostream : public basic_istream<Elem, Tr>,  
    public basic_ostream<Elem, Tr>  
{  
public:  
    explicit basic_iostream(basic_streambuf<Elem, Tr>* strbuf);

    virtual ~basic_iostream();

};  
```  
  
## <a name="remarks"></a>備註  
 此樣板類別描述透過其基底類別 [basic_ostream](../standard-library/basic-ostream-class.md)< `Elem`, `Tr`> 控制插入的物件，和透過其基底類別 [basic_istream](../standard-library/basic-istream-class.md)< `Elem`, `Tr`> 擷取的物件。 兩個物件共用通用的虛擬基底類別 [basic_ios](../standard-library/basic-ios-class.md)< `Elem`, `Tr`>。 它們也會以 `Elem` 類型的項目 (其字元特性由類別 `Tr` 決定) 管理通用的資料流緩衝區。 此建構函式會藉由 `basic_istream`( **strbuf**) 和 `basic_ostream`( **strbuf**) 初始化其基底類別。  
  
### <a name="constructors"></a>建構函式  
  
|||  
|-|-|  
|[basic_iostream](#basic_iostream)|建立 `basic_iostream` 物件。|  
  
### <a name="member-functions"></a>成員函式  
  
|||  
|-|-|  
|[swap](#swap)|將提供之 `basic_iostream` 物件的內容與此物件的內容交換。|  
  
### <a name="operators"></a>運算子  
  
|||  
|-|-|  
|[operator=](#op_eq)|將指定的 `basic_iostream` 物件值指派給這個物件。 這是一個移動指派，涉及不會留下複本的 `rvalue`。|  
  
## <a name="requirements"></a>需求  
 **標頭︰**\<istream>  
  
 **命名空間：** std  
  
##  <a name="basic_iostream"></a>  basic_iostream::basic_iostream  
 建立 `basic_iostream` 物件。  
  
```  
explicit basic_iostream(basic_streambuf<Elem, Tr>* strbuf);

basic_iostream(basic_iostream&& right);

basic_iostream();
```  
  
### <a name="parameters"></a>參數  
 `strbuf`  
 現有的 `basic_streambuf` 物件。  
  
 `right`  
 現有的 `basic_iostream` 物件，用來建構新的 `basic_iostream`。  
  
### <a name="remarks"></a>備註  
 第一個建構函式會藉由 `basic_istream(strbuf)` 和 `basic_ostream(strbuf)` 初始化基底物件。  
  
 第二個建構函式呼叫來初始化基底物件`move(right)`。  
  
##  <a name="op_eq"></a>  basic_iostream::operator=  
 將指定的 `basic_iostream` 物件值指派給這個物件。 這是一個移動指派，涉及不會留下複本的右值。  
  
```  
basic_iostream& operator=(basic_iostream&& right);
```  
  
### <a name="parameters"></a>參數  
 `right`  
 要指派之來源 `basic_iostream` 物件的 `rvalue` 參考。  
  
### <a name="remarks"></a>備註  
 此成員運算子會呼叫`swap(right)`。  
  
##  <a name="swap"></a>  basic_iostream::swap  
 將提供之 `basic_iostream` 物件的內容與此物件的內容交換。  
  
```  
void swap(basic_iostream& right);
```  
  
### <a name="parameters"></a>參數  
 `right`  
 要交換的 `basic_iostream` 物件。  
  
### <a name="remarks"></a>備註  
 成員函式呼叫`swap(right)`。  
  
## <a name="see-also"></a>請參閱  
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 程式設計](../standard-library/iostream-programming.md)   
 [iostream 慣例](../standard-library/iostreams-conventions.md)

