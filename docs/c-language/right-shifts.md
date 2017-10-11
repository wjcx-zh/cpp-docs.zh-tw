---
title: "右移位 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: c878e97d-ea3c-4c6b-90a8-b1b24b2d5b19
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: cee551dfd0dbac11110a945edee21af6636138bc
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="right-shifts"></a>右移位
負值帶正負號的整數類資料類型向右移位的結果  
  
 將負值向右移位會產生絕對值的一半 (無條件捨去)。 例如，-253 的帶正負號 `short` 值 (十六進位 0xFF03、二進位 11111111 00000011) 向右移位一個位元會產生 -127 (十六進位 0xFF81、二進位 11111111 10000001)。 正 253 向右移位會產生 +126。  
  
 向右移位會保留帶正負號之整數類資料類型的正負號位元。 當帶正負號的整數向右移位時，最高有效位元會保持原位。 例如，如果 0xF0000000 為帶正負號的 `int`，向右移位會產生 0xF8000000。 負 `int` 向右移位 32 次會產生 0xFFFFFFFF。  
  
 當不帶正負號的整數向右移位時，會清除最高有效位元。 例如，如果 0xF000 不帶正負號，結果是 0x7800。 `unsigned` 或正 `int` 向右移位 32 次會產生 0x00000000。  
  
## <a name="see-also"></a>另請參閱  
 [整數](../c-language/integers.md)
