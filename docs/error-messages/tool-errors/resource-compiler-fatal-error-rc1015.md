---
title: 資源編譯器嚴重錯誤 RC1015 |Microsoft Docs
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
ms.openlocfilehash: 0456845152fb2879d2f58c9c40af2562c7207535
ms.sourcegitcommit: d3c41b16bf05af2149090e996d8e71cd6cd55c7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2018
ms.locfileid: "48890240"
---
# <a name="resource-compiler-fatal-error-rc1015"></a>資源編譯器嚴重錯誤 RC1015

無法開啟 include 檔 'filename' 嗎

指定的 include 檔案不存在、 無法開啟，或找不到。

請確定環境設定有效，而且指定的檔案路徑正確。 請確定足夠的檔案控制代碼可用於資源編譯器。 如果檔案位於網路磁碟機，請確定您有開啟檔案的權限。

即使 Include 檔存在於指定的其他 Include 目錄中 ([組態屬性] -> [資源] -> [一般] 屬性頁)，也可能發生 RC1015；請指定 Include 檔的完整路徑。
