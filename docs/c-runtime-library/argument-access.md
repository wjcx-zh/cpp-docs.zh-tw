---
title: "引數存取 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.arguments
dev_langs:
- C++
helpviewer_keywords:
- argument access macros [C++]
- variable-length argument lists
ms.assetid: 7046ae34-a0ec-44f0-815d-3209492a3e19
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: c216c009d84771fdf34426b6121a89eb4b3f73e4
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="argument-access"></a>引數存取
`va_arg`、`va_end` 和 `va_start` 巨集能在引數數目為變數時，提供函式引數的存取。 這些巨集定義在 STDARG.H 以便與 ANSI C 相容，以及定義在 VARARGS.H 以便與 UNIX System V 相容。  
  
### <a name="argument-access-macros"></a>引數存取巨集  
  
|巨集|用法|  
|-----------|-------------------------------|  
|[va_arg](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|從清單中擷取引數|  
|[va_end](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|重設指標|  
|[va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|將指標設定至引數清單的開頭|  
  
## <a name="see-also"></a>另請參閱  
 [依類別區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)
