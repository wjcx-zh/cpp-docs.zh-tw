---
title: 整數值的範圍 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 0e9c6161-8f3f-4bfb-9fcc-a6c8dc97d702
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2695b5d2a006529042453b7048bec400388fb74b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="range-of-integer-values"></a>整數值的範圍
**ANSI 3.1.2.5**：各種整數類型值的表示和設定  
  
 整數包含 32 個位元 (四個位元組)。 帶正負號的整數以二補數格式表示。 最高有效位元會保存此正負號：1 為負數，0 為正數及零。 其值如下所列：  
  
|類型|最小和最大值|  
|----------|-------------------------|  
|**unsigned short**|0 到 65535|  
|`signed short`|-32768 到 32767|  
|`unsigned long`|0 到 4294967295|  
|**signed long**|-2147483648 到 2147483647|  
  
## <a name="see-also"></a>請參閱  
 [整數](../c-language/integers.md)