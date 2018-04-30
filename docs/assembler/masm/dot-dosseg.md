---
title: .DOSSEG | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .DOSSEG
dev_langs:
- C++
helpviewer_keywords:
- .DOSSEG directive
ms.assetid: 175ad470-0a2b-4e2b-b078-65e224fec040
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3817cfe98758faf86ea87d74e02657598c3e806b
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="dosseg"></a>.DOSSEG
排序依據 MS-DOS 區段慣例區段： 程式碼第一次，然後區段不在 DGROUP，和在 DGROUP 然後區段。  
  
## <a name="syntax"></a>語法  
  
```  
  
.DOSSEG  
  
```  
  
## <a name="remarks"></a>備註  
 DGROUP 中的區段，請遵循此順序： 區段不在 BSS 或堆疊，BSS 區段，然後按一下最後堆疊區段。 主要用來確定可持續 MASM 獨立程式中的 CodeView 支援。 與相同[DOSSEG](../../assembler/masm/dosseg.md)。  
  
## <a name="see-also"></a>另請參閱  
 [指示詞參考](../../assembler/masm/directives-reference.md)