---
title: 定義和慣例 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- nonterminals definition
ms.assetid: f9b3cf5f-6a7c-4a10-9b18-9d4a43efdaeb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 99f227f37f4a9de92f244df5988f7ee8088e41d5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32384142"
---
# <a name="definitions-and-conventions"></a>定義和慣例
終端是語法定義的端點。 沒有其他解決方式。 終端包括一組保留字和使用者定義的識別項。  
  
 非終端是語法中的預留位置，會在此語法摘要中的其他地方定義。 定義可以是遞迴式。  
  
 選擇性的元件會以下標的 opt 表示。 例如，套用至物件的  
  
```  
  
{  
expression <SUB>opt</SUB> }  
```  
  
 表示放在大括號中的選擇性運算式。  
  
 語法慣例會針對語法的不同元件使用不同的字型屬性。 符號和字型如下：  
  
|屬性|描述|  
|---------------|-----------------|  
|*nonterminal*|斜體類型表示非終端項。|  
|**const**|粗體類型的終端項為必須依下述方式輸入的常值保留字和符號。 此內容中的字元一律區分大小寫。|  
|opt|後面接著非終端項的 opt 一律為選擇項。|  
|預設字樣|這個字樣中描述或列出的集合中的字元可用來作為 C 陳述式中的終端。|  
  
 接著非終端項的冒號 (**:**) 會引入其定義。 除非前面加上「one of」字樣，否則替代定義另列於其他行。  
  
## <a name="see-also"></a>請參閱  
 [C 語言語法摘要](../c-language/c-language-syntax-summary.md)