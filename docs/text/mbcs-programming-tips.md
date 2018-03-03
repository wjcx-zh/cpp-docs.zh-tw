---
title: "MBCS 程式設計提示 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _mbcs
dev_langs:
- C++
helpviewer_keywords:
- programming [C++], MBCS
- character sets [C++], multibyte
- MBCS [C++], programming
- multibyte characters [C++]
ms.assetid: d8ad36b8-917f-474e-8adb-69462adecd17
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1dc9c5dfd0dafe96e2d37b789b64c8215aa454e3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="mbcs-programming-tips"></a>MBCS 程式設計提示
在新的開發，您應該為終端使用者可能看到的所有字串使用 Unicode 字元編碼。 MBCS 是由 Unicode 取代的舊版技術。 本節為必須維護使用 MBCS 且不適合轉換為 Unicode 之現有程式的開發人員提供提示。 此建議適用於 MFC 應用程式和撰寫而非 MFC 應用程式。 主題包括：  
  
-   [一般 MBCS 程式設計的建議](../text/general-mbcs-programming-advice.md)  
  
-   [增量和遞減指標](../text/incrementing-and-decrementing-pointers.md)  
  
-   [位元組索引](../text/byte-indices.md)  
  
-   [字串中的最後一個字元](../text/last-character-in-a-string.md)  
  
-   [字元指派](../text/character-assignment.md)  
  
-   [字元比較](../text/character-comparison.md)  
  
-   [緩衝區溢位](../text/buffer-overflow.md)  
  
## <a name="see-also"></a>請參閱  
 [多位元組字元集 (MBCS) 的支援](../text/support-for-multibyte-character-sets-mbcss.md)