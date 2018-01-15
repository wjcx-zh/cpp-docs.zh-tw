---
title: "Null 和未定義的巨集 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- NMAKE program, undefined macros
- Null macros in NMAKE
- macros, null and undefined
- undefined macros and NMAKE
- NMAKE program, null macros
ms.assetid: 1db4611a-1755-4328-b00f-d35365af8b6c
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9581b152057655c510f1cbcd4ab29ba8339070b8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="null-and-undefined-macros"></a>Null 和未定義的巨集
Null 和未定義的巨集展開為 null 的字串，但巨集定義為 null 的字串會被視為前置處理運算式中定義。 若要定義巨集做為 null 的字串，指定沒有字元除了命令列或命令檔中的等號 （=） 後面的空格或定位字元和雙引號括住的 null 字串或定義 ("")。 若要取消定義巨集，使用**！UNDEF。** 如需詳細資訊，請參閱[Makefile 前置處理指示詞](../build/makefile-preprocessing-directives.md)。  
  
## <a name="see-also"></a>請參閱  
 [定義 NMAKE 巨集](../build/defining-an-nmake-macro.md)