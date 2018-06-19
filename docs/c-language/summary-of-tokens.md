---
title: 語彙基元摘要 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 2978cbf6-e66e-46fc-9938-caa052f2ccf7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 936807fef6b74ccb081bf15d7314da14f064fb7a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32389110"
---
# <a name="summary-of-tokens"></a>語彙基元摘要
*token*:  
 *keyword*  
  
 *identifier*  
  
 *constant*  
  
 *string-literal*  
  
 *operator*  
  
 `punctuator`  
  
 *preprocessing-token*:  
 *header-name*  
  
 *identifier*  
  
 *pp-number*  
  
 *character-constant*  
  
 *string-literal*  
  
 *operator punctuator*  
  
 不可是上述任一個的每個非空白字元  
  
 *header-name*:  
 **\<**  *path-spec*  **> "**  *path spec*  **"**  
  
 *path-spec*:  
 合法的檔案路徑  
  
 *pp-number*:  
 *digit*  
  
 **.** *digit*  
  
 *pp-number digit*  
  
 *pp-number nondigit*  
  
 *pp-number*  **e**  *sign*  
  
 *pp-number*  **E**  *sign*  
  
 *pp-number*  **.**  
  
## <a name="see-also"></a>請參閱  
 [語彙文法](../c-language/lexical-grammar.md)