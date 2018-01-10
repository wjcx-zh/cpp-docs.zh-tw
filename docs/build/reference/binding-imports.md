---
title: "繫結匯入 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- /DELAY:NOBIND linker option
- DELAY:NOBIND linker option
ms.assetid: bb766038-deb1-41b1-bcbc-29a30e8c1e2a
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4f462eeea9f2bca566745d425b84bd1506f52fc8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="binding-imports"></a>繫結匯入
連結器預設行為是建立可繫結的匯入位址表延遲載入 dll。 如果 DLL 已繫結，則 helper 函式會嘗試使用的繫結的資訊，而不是呼叫**GetProcAddress**上每一個參考匯入。 如果時間戳記或慣用的位址不相符所載入的 DLL，則 helper 函式假設繫結匯的入位址表已過期，而不存在，會繼續。  
  
 如果您不想要繫結 DLL 的延遲載入匯入，則指定[/延遲](../../build/reference/delay-delay-load-import-settings.md): nobind 連結器的命令列上將導致繫結匯的入位址表映像檔中的產生和取用的空間。  
  
## <a name="see-also"></a>請參閱  
 [延遲載入 DLL 的連結器支援](../../build/reference/linker-support-for-delay-loaded-dlls.md)