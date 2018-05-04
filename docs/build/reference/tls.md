---
title: -TLS |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /TLS
dev_langs:
- C++
helpviewer_keywords:
- /TLS dumpbin option
- -TLS dumpbin option
ms.assetid: 2b3f48f9-cac4-4351-b15c-2833b43bc709
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b5e510f406ceae7508f9b84f99e7ab397d22f114
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="tls"></a>/TLS
顯示從可執行檔的 IMAGE_TLS_DIRECTORY 結構。  
  
## <a name="remarks"></a>備註  
 / TLS 顯示 TLS 結構的欄位以及 TLS 回呼函式的位址。  
  
 如果程式不會使用執行緒區域儲存區，其映像不會包含 TLS 結構。  請參閱[執行緒](../../cpp/thread.md)如需詳細資訊。  
  
 IMAGE_TLS_DIRECTORY winnt.h 中定義。  
  
## <a name="see-also"></a>另請參閱  
 [DUMPBIN 選項](../../build/reference/dumpbin-options.md)