---
title: 繫結匯入 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- /DELAY:NOBIND linker option
- DELAY:NOBIND linker option
ms.assetid: bb766038-deb1-41b1-bcbc-29a30e8c1e2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7519fb18ac7f24e79a5f7f664cb35f8eb5b3fd77
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368924"
---
# <a name="binding-imports"></a>繫結匯入
連結器預設行為是建立可繫結的匯入位址表延遲載入 dll。 如果 DLL 已繫結，則 helper 函式會嘗試使用的繫結的資訊，而不是呼叫**GetProcAddress**上每一個參考匯入。 如果時間戳記或慣用的位址不相符所載入的 DLL，則 helper 函式假設繫結匯的入位址表已過期，而不存在，會繼續。  
  
 如果您不想要繫結 DLL 的延遲載入匯入，則指定[/延遲](../../build/reference/delay-delay-load-import-settings.md): nobind 連結器的命令列上將導致繫結匯的入位址表映像檔中的產生和取用的空間。  
  
## <a name="see-also"></a>另請參閱  
 [延遲載入 DLL 的連結器支援](../../build/reference/linker-support-for-delay-loaded-dlls.md)