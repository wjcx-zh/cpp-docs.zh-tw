---
title: "命令巨集和選項巨集 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- options macros
- command macros in NMAKE
- macros, options macros
- macros, command macros
ms.assetid: 50dff03c-0dc3-4a8a-9a17-57e0e4ea9bac
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 06f5d48395c0395a85c90096bf2dbad8627ac41a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="command-macros-and-options-macros"></a>命令巨集和選項巨集
命令巨集是預先定義的 Microsoft 產品。 選項巨集代表這些產品的選項，並預設為未定義。 同時預先定義的推斷規則中使用，而且可以用於描述區塊或使用者定義的推斷規則。 命令巨集可以重新定義，來表示部分或全部的命令列，包括選項。 如果未定義選項巨集就會產生 null 字串。  
  
|Microsoft 產品|命令巨集|定義為|選項巨集|  
|-----------------------|-------------------|----------------|-------------------|  
|巨集組合語言|**做為**|ml|**AFLAGS**|  
|基本編譯器|**BC**|bc|**BFLAGS**|  
|C 編譯器|**[副本]**|cl|**CFLAGS**|  
|C++ 編譯器|**CPP**|cl|**CPPFLAGS**|  
|C++ 編譯器|**CXX**|cl|**CXXFLAGS**|  
|資源編譯器|**RC**|rc|**RFLAGS**|  
  
## <a name="see-also"></a>請參閱  
 [特殊的 NMAKE 巨集](../build/special-nmake-macros.md)