---
title: "資源編譯器嚴重錯誤 RC1015 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- RC1015
dev_langs:
- C++
helpviewer_keywords:
- RC1015
ms.assetid: 23f187e1-5538-40b5-9042-edd2888f55c2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 666221cf5c3e812cd856271ea97cf4966383ec20
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="resource-compiler-fatal-error-rc1015"></a>資源編譯器嚴重錯誤 RC1015
無法開啟 include 檔 'filename' 嗎  
  
 指定的 include 檔不存在、 無法開啟或找不到。  
  
 請確定環境設定有效，而且指定的檔案路徑正確。 請確定資源編譯器可使用足夠的檔案控制代碼。 如果檔案位於網路磁碟機上，請確定您有權限來開啟檔案。  
  
 即使 Include 檔存在於指定的其他 Include 目錄中 ([組態屬性] -> [資源] -> [一般] 屬性頁)，也可能發生 RC1015；請指定 Include 檔的完整路徑。  
  
 如需詳細資訊，請參閱知識庫文章 Q326987: RC1015 錯誤時使用資源檢視 Include 路徑是否太長。