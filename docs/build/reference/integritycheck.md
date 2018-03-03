---
title: "/INTEGRITYCHECK |Microsoft 文件"
ms.custom: 
ms.date: 12/28/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /INTEGRITYCHECK
dev_langs:
- C++
helpviewer_keywords:
- -INTEGRITYCHECK editbin options
- /INTEGRITYCHECK editbin options
- INTEGRITYCHECK editbin options
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 99caec18162a7506b8b7a467eb7374b6fe4a38d9
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2018
---
# <a name="integritycheck"></a>/INTEGRITYCHECK

指定必須檢查在載入時間的二進位檔映像的數位簽章。

> **/INTEGRITYCHECK**[**: NO**]

## <a name="remarks"></a>備註

在頁首中的可執行檔的 DLL 檔案，這個選項會設定需要載入的映像中 Windows 記憶體管理員進行數位簽章檢查的旗標。 在 Windows Vista 之前的 Windows 版本會忽略此旗標。 適用於 64 位元 Dll 實作核心模式程式碼，而且建議所有的裝置驅動程式，必須設定這個選項。 如需詳細資訊，請參閱[核心模式程式碼簽署需求](/windows-hardware/drivers/install/kernel-mode-code-signing-requirements--windows-vista-and-later-)。

## <a name="see-also"></a>另請參閱

[EDITBIN 選項](../../build/reference/editbin-options.md)  
