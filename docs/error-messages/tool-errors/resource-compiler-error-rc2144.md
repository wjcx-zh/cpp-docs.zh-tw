---
title: "資源編譯器錯誤 RC2144 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- RC2144
dev_langs:
- C++
helpviewer_keywords:
- RC2144
ms.assetid: 1b3ff39a-92cd-4a04-b1a3-b1fa6a805813
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c29a1c1f392372b8dfddd84fa9693010e6a52bfa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="resource-compiler-error-rc2144"></a>資源編譯器錯誤 RC2144
PRIMARY LANGUAGE ID 不是數字  
  
 PRIMARY LANGUAGE ID 必須是十六進位語言 ID。 請參閱[語言和國家/地區字串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)中*執行階段程式庫參考*有效語言 Id 的清單。  
  
 如果已在 .RC 檔案中使用工具加入和刪除資源，也會發生此錯誤。 若要修正這個問題，請在文字編輯器中開啟 .RC 檔案，並以手動方式清除任何未使用的資源。