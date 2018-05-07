---
title: 資源編譯器嚴重錯誤 RC1015 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC1015
dev_langs:
- C++
helpviewer_keywords:
- RC1015
ms.assetid: 23f187e1-5538-40b5-9042-edd2888f55c2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b7744242e44ecfc72ee57ab979969ad81b209e57
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="resource-compiler-fatal-error-rc1015"></a>資源編譯器嚴重錯誤 RC1015
無法開啟 include 檔 'filename' 嗎  
  
 指定的 include 檔不存在、 無法開啟或找不到。  
  
 請確定環境設定有效，而且指定的檔案路徑正確。 請確定資源編譯器可使用足夠的檔案控制代碼。 如果檔案位於網路磁碟機上，請確定您有權限來開啟檔案。  
  
 即使 Include 檔存在於指定的其他 Include 目錄中 ([組態屬性] -> [資源] -> [一般] 屬性頁)，也可能發生 RC1015；請指定 Include 檔的完整路徑。  
  
 如需詳細資訊，請參閱知識庫文章 Q326987: RC1015 錯誤時使用資源檢視 Include 路徑是否太長。