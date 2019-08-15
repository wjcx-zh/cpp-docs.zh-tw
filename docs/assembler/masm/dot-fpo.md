---
title: .FPO
ms.date: 08/30/2018
f1_keywords:
- .FPO
helpviewer_keywords:
- .FPO directive
ms.assetid: 35f4cd61-32f9-4262-b657-73f04f775d09
ms.openlocfilehash: b793b3efa72a676b800c10b98ea06001ddcf10d5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491427"
---
# <a name="fpo"></a>.FPO

該.FPO 指示詞會控制將 debug 記錄發出至 debug $ F 區段或區段。

## <a name="syntax"></a>語法

> FPO (*cdwLocals*、 *cdwParams*、 *cbProlog*、 *cbRegs*、 *fUseBP*、 *cbFrame*)

### <a name="parameters"></a>參數

*cdwLocals*<br/>
本機變數的數目, 不帶正負號的32位值。

*cdwParams*<br/>
DWORD 中的參數大小, 不帶正負號的16位值。

*cbProlog*<br/>
函數初構程式碼中的位元組數目, 不帶正負號的8位值。

*cbRegs*<br/>
已儲存的數位暫存器。

*fUseBP*<br/>
指出是否已配置 EBP 暫存器。 為0或1。

*cbFrame*<br/>
表示框架類型。  如需詳細資訊, 請參閱[FPO_DATA](/windows/win32/api/winnt/ns-winnt-fpo_data) 。

## <a name="see-also"></a>另請參閱

[指示詞參考](../../assembler/masm/directives-reference.md)<br/>
