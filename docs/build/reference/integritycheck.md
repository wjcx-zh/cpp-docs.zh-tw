---
title: /INTEGRITYCHECK
ms.date: 12/28/2017
f1_keywords:
- /INTEGRITYCHECK
helpviewer_keywords:
- -INTEGRITYCHECK editbin options
- /INTEGRITYCHECK editbin options
- INTEGRITYCHECK editbin options
ms.openlocfilehash: b3f6622e3628db53c363b239c59accd94f708ab0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50617265"
---
# <a name="integritycheck"></a>/INTEGRITYCHECK

指定必須檢查在載入時間的二進位檔映像的數位簽章。

> **/INTEGRITYCHECK**[**: NO**]

## <a name="remarks"></a>備註

在 DLL 或可執行檔的標頭，這個選項會設定旗標，需要將影像載入 Windows 中的記憶體管理員檢查數位簽章。 在 Windows Vista 之前的 Windows 版本會忽略此旗標。 適用於 64 位元 Dll 實作核心模式程式碼，並建議用於所有裝置驅動程式，就必須設定這個選項。 如需詳細資訊，請參閱 <<c0> [ 核心模式程式碼簽署需求](/windows-hardware/drivers/install/kernel-mode-code-signing-requirements--windows-vista-and-later-)。

## <a name="see-also"></a>另請參閱

[EDITBIN 選項](../../build/reference/editbin-options.md)
