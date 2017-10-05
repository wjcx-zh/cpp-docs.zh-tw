---
title: "regex_error 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- regex/std::regex_error
- regex/std::regex_error::code
dev_langs:
- C++
helpviewer_keywords:
- regex_error class
ms.assetid: 3333a1a3-ca6f-4612-84b2-1b4c7e3db5a4
caps.latest.revision: 19
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
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: a0336bce168edc8b4c50639b1e3ace4f82e7c971
ms.contentlocale: zh-tw
ms.lasthandoff: 10/03/2017

---
# <a name="regexerror-class"></a>regex_error 類別
回報錯誤的 basic_regex 物件。  
  
## <a name="syntax"></a>語法  
  
```  
class regex_error  
 : public std::runtime_error {  
public:  
    explicit regex_error(regex_constants::error_code error);

    regex_constants::error_code code() const;

 
 };  
```  
  
## <a name="remarks"></a>備註  
 此類別描述為了回報建構或使用 `basic_regex` 物件時所發生的錯誤，所擲回的例外狀況物件。  
  
## <a name="requirements"></a>需求  
 **標頭︰**\<regex>  
  
 **命名空間：** std  
  
##  <a name="code"></a>  regex_error::code  
 傳回錯誤碼。  
  
```  
regex_constants::error_code code() const;
```  
  
### <a name="remarks"></a>備註  
 成員函式會傳回傳遞給物件建構函式的值。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__regex__regex_error_code.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex_error paren(std::regex_constants::error_paren);   
  
    try   
        {   
        std::regex rx("(a");   
        }   
    catch (const std::regex_error& rerr)   
        {   
        std::cout << "regex error: "   
            << (rerr.code() == paren.code()   
                 "unbalanced parentheses" : "")   
            << std::endl;   
        }   
    catch (...)   
        {   
        std::cout << "unknown exception" << std::endl;   
        }   
  
    return (0);   
    }  
  
```  
  
```Output  
regex error: unbalanced parentheses  
```  
  
##  <a name="regex_error"></a>  regex_error::regex_error  
 建構物件。  
  
```  
regex_error(regex_constants::error_code error);
```  
  
### <a name="parameters"></a>參數  
 `error`  
 錯誤碼。  
  
### <a name="remarks"></a>備註  
 建構函式會建構物件以保留 `error`值。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__regex__regex_error_construct.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex_error paren(std::regex_constants::error_paren);   
  
    try   
        {   
        std::regex rx("(a");   
        }   
    catch (const std::regex_error& rerr)   
        {   
        std::cout << "regex error: "   
            << (rerr.code() == paren.code()   
                 "unbalanced parentheses" : "")   
            << std::endl;   
        }   
    catch (...)   
        {   
        std::cout << "unknown exception" << std::endl;   
        }   
  
    return (0);   
    }  
  
```  
  
```Output  
regex error: unbalanced parentheses  
```  
  
## <a name="see-also"></a>另請參閱  
[\<regex>](../standard-library/regex.md)  
[regex_constants 類別](../standard-library/regex-constants-class.md)  
[\<regex> 函式](../standard-library/regex-functions.md)  
[regex_iterator 類別](../standard-library/regex-iterator-class.md)  
[\<regex> 運算子](../standard-library/regex-operators.md)  
[regex_token_iterator 類別](../standard-library/regex-token-iterator-class.md)  
[regex_traits 類別](../standard-library/regex-traits-class.md)  
[\<regex> typedefs](../standard-library/regex-typedefs.md)  

