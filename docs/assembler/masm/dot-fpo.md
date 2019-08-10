---
title: .FPO
ms.date: 08/30/2018
f1_keywords:
- .FPO
helpviewer_keywords:
- .FPO directive
ms.assetid: 35f4cd61-32f9-4262-b657-73f04f775d09
ms.openlocfilehash: 3bdb6af98aa71fef3d4af24091dc7463d917ce15
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915954"
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
表示框架類型。  如需詳細資訊, 請參閱[FPO_DATA](/windows/desktop/api/winnt/ns-winnt-fpo_data) 。

## <a name="see-also"></a>另請參閱

[指示詞參考](../../assembler/masm/directives-reference.md)<br/>
