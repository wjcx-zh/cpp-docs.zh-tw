---
title: 嚴重錯誤 C1854 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- devlang-cpp
ms.topic: error-reference
f1_keywords:
- C1854
dev_langs:
- C++
helpviewer_keywords:
- C1854
ms.assetid: 8c21a9cc-1737-475c-9e57-8725cd8937c1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e517832720e31bfae88e79ad879f1427b9c25a48
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33230235"
---
# <a name="fatal-error-c1854"></a>嚴重錯誤 C1854
  
> 無法覆寫在目的檔中先行編譯標頭建立期間形成的資訊: '*filename*'  
  
您指定[/Yu （使用先行編譯標頭檔）](../../build/reference/yu-use-precompiled-header-file.md)選項之後指定[/Yc （建立先行編譯標頭檔）](../../build/reference/yc-create-precompiled-header-file.md)在同一個檔案的選項。  
  
若要修正此問題，在一般情況下，只能有一個檔案中設定您的專案編譯所 **/Yc**選項，然後將編譯使用所有其他檔案設定 **/Yu**選項。 如需詳細資訊，使用 **/Yc**選項，以及如何設定 Visual Studio IDE 中，請參閱[/Yc （建立先行編譯標頭檔）](../../build/reference/yc-create-precompiled-header-file.md)。 如需有關使用先行編譯標頭的詳細資訊，請參閱[建立先行編譯標頭檔](../../build/reference/creating-precompiled-header-files.md)。  
