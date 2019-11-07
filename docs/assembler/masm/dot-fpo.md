---
title: .FPO
ms.date: 11/05/2019
f1_keywords:
- .FPO
helpviewer_keywords:
- .FPO directive
ms.assetid: 35f4cd61-32f9-4262-b657-73f04f775d09
ms.openlocfilehash: 3938d9194c35d567ea670e0b92a731193ccd2254
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/06/2019
ms.locfileid: "73703788"
---
# <a name="fpo-32-bit-masm"></a>.FPO （32位 MASM）

該.FPO 指示詞會控制將 debug 記錄發出至 debug $ F 區段或區段。 （僅限 32-bit MASM）。

## <a name="syntax"></a>語法

> FPO （*cdwLocals*、 *cdwParams*、 *cbProlog*、 *cbRegs*、 *fUseBP*、 *cbFrame*）

### <a name="parameters"></a>參數

*cdwLocals*<br/>
本機變數的數目，不帶正負號的32位值。

*cdwParams*<br/>
DWORD 中的參數大小，不帶正負號的16位值。

*cbProlog*<br/>
函數初構程式碼中的位元組數目，不帶正負號的8位值。

*cbRegs*<br/>
已儲存的數位暫存器。

*fUseBP*<br/>
指出是否已配置 EBP 暫存器。 為0或1。

*cbFrame*<br/>
表示框架類型。  如需詳細資訊，請參閱[FPO_DATA](/windows/win32/api/winnt/ns-winnt-fpo_data) 。

## <a name="see-also"></a>請參閱

[指示詞參考](../../assembler/masm/directives-reference.md)<br/>
