---
title: 二元運算子 |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- member-selection operators [C++]
- operators [C++], binary
- binary operators [C++]
ms.assetid: c0e7fbff-bc87-4708-8333-504ac09ee83e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6c5ad5997657ce9f8a61383a2cd7e685f0a28751
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036549"
---
# <a name="binary-operators"></a>二元運算子

下表顯示可以多載的運算子清單。

## <a name="redefinable-binary-operators"></a>可重新定義的二元運算子

|運算子|名稱|
|--------------|----------|
|**、**|逗號|
|**\!=**|不等|
|**%**|模數|
|**%=**|模數/指派|
|**&**|位元 AND|
|**&&**|邏輯 AND|
|**&=**|位元 AND/指派|
|**&#42;**|乘法|
|**&#42;=**|乘法/指派|
|**+**|加入|
|**+=**|加法/指派|
|**-**|減法|
|**-=**|減法/指派|
|**->**|成員選取|
|**->&#42;**|成員指標選取|
|**/**|除號|
|**/=**|除法/指派|
|**<**|小於|
|**<<**|左移|
|**<<=**|左移/指派|
|**<=**|小於或等於|
|**=**|指派|
|**==**|相等|
|**>**|大於|
|**>=**|大於或等於|
|**>>**|右移|
|**>>=**|右移/指派|
|**^**|互斥 OR|
|**^=**|互斥 OR/指派|
|**&#124;**|位元包含 OR|
|**&#124;=**|位元包含 OR/指派|
|**&#124;&#124;**|邏輯 OR|

若要將二元運算子函式宣告為非靜態成員，您必須以此格式進行宣告：

> *ret 型別***運算子** *op* **(** *arg* **)**

何處*ret 類型*是傳回的型別， *op*是其中一個列在上表中，運算子和*arg*是任何類型的引數。

若要將二元運算子函式宣告為全域函式，您必須以此格式進行宣告：

> *ret 型別***運算子** *op* **(** _arg1_**，** _arg2_**)**

其中*ret 類型*並*op*成員運算子函式中所述和*arg1*並*arg2*引數。 至少要有一個引數是類別類型。

> [!NOTE]
> 二元運算子的傳回型別不受限制；不過，大部分使用者定義的二元運算子會傳回類別類型或類別類型的參考。

## <a name="see-also"></a>另請參閱

[運算子多載](../cpp/operator-overloading.md)