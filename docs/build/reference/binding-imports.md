---
title: 繫結匯入 |Microsoft Docs
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
ms.openlocfilehash: 551028999d11379c06d3319f01e882a33ad57936
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705194"
---
# <a name="binding-imports"></a>繫結匯入

預設的連結器行為是建立延遲載入 dll 的可繫結的匯入位址表格。 如果已繫結 DLL，helper 函式會嘗試使用的繫結的資訊，而不是呼叫**GetProcAddress**上每個參考匯入。 如果時間戳記或慣用的位址不相符所載入的 DLL，helper 函式假設繫結的匯入位址表格已過期，並將繼續如同它不存在。

如果您根本不打算將 DLL 的延遲載入匯入繫結，則指定[/延遲](../../build/reference/delay-delay-load-import-settings.md): nobind 連結器的命令列上會防止繫結的匯入位址表格映像檔中的產生和取用的空間。

## <a name="see-also"></a>另請參閱

[延遲載入 DLL 的連結器支援](../../build/reference/linker-support-for-delay-loaded-dlls.md)