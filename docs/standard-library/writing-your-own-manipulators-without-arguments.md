---
title: "撰寫不含引數的操作工具 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- manipulators
ms.assetid: 2dc62d09-45b7-454d-bd9d-55f3c72c206d
caps.latest.revision: 8
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
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 276bba3dd5ce5debd926ebbc4ccfaf52c6b92097
ms.lasthandoff: 02/24/2017

---
# <a name="writing-your-own-manipulators-without-arguments"></a>撰寫不含引數的操作工具
撰寫不使用引數的操作工具，不需要衍生類別，也不需要使用複雜的巨集。 假設您的印表機需要一組 \<ESC>[ 以進入粗體模式。 您可以將這組直接插入資料流：  
  
```  
cout <<"regular " <<'\033' <<'[' <<"boldface" <<endl;  
```  
  
 或者，您可以定義 `bold` 操作工具來插入字元：  
  
```  
ostream& bold(ostream& os) {  
    return os <<'\033' <<'[';  
}  
cout <<"regular " <<bold <<"boldface" <<endl;  
```  
  
 全域定義的 `bold` 函式會接受 `ostream` 參考引數，並傳回 `ostream` 參考。 它不是成員函式或 Friend，因為它不需要存取任何私用類別項目。 `bold` 函式會使用如下的宣告來連接到資料流，因為已多載資料流的 `<<` 運算子來接受該類型的函式：  
  
```  
_Myt& operator<<(ios_base& (__cdecl *_Pfn)(ios_base&))  
{     // call ios_base manipulator  
 (*_Pfn)(*(ios_base *)this);

    return (*this);

}  
```  
  
 您可以使用此功能來擴充其他多載的運算子。 在此案例中，`bold` 一定會將字元插入資料流。 函式會在將它插入資料流時呼叫，但在列印相鄰字元時並不需要。 因此，列印可能會因為資料流的緩衝區而延遲。  
  
## <a name="see-also"></a>另請參閱  
 [輸出資料流](../standard-library/output-streams.md)


