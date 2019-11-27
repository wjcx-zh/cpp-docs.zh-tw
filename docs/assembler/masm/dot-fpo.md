---
title: .FPO
ms.date: 11/05/2019
f1_keywords:
- .FPO
helpviewer_keywords:
- .FPO directive
ms.assetid: 35f4cd61-32f9-4262-b657-73f04f775d09
ms.openlocfilehash: 650c69be17c9271c343360edbb90f093841a1047
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74398249"
---
# <a name="fpo-32-bit-masm"></a>.FPO （32位 MASM）

**。FPO**指示詞會控制將 debug 記錄發出至 debug $ F 區段或區段。 （僅限 32-bit MASM）。

## <a name="syntax"></a>語法

> **.FPO** （*cdwLocals*、 *cdwParams*、 *cbProlog*、 *cbRegs*、 *fUseBP*、 *cbFrame*）

### <a name="parameters"></a>參數

*cdwLocals*\
本機變數的數目，不帶正負號的32位值。

*cdwParams*\
DWORD 中的參數大小，不帶正負號的16位值。

*cbProlog*\
函數初構程式碼中的位元組數目，不帶正負號的8位值。

*cbRegs*\
已儲存的數位暫存器。

*fUseBP*\
指出是否已配置 EBP 暫存器。 為0或1。

*cbFrame*\
表示框架類型。  如需詳細資訊，請參閱[FPO_DATA](/windows/win32/api/winnt/ns-winnt-fpo_data) 。

## <a name="see-also"></a>另請參閱

[指示詞參考](directives-reference.md)
