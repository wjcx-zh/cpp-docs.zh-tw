---
title: 使用 Template Library (ATL) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- template libraries
ms.assetid: 5e80ec6e-a61c-41ce-b34b-9a6252c46265
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 91a9c10bef285780ded145e33800ebd3db198827
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43754780"
---
# <a name="using-a-template-library"></a>使用範本程式庫

範本有些許類似巨集。 使用巨集，因為叫用範本會使它 （使用適當的參數替代） 依序展開您所撰寫的程式碼。 不過，樣板更進一步這可讓您當做參數傳遞的類型為基礎的新類別的建立。 這些新的類別會實作型別安全方式來執行您的範本程式碼所編寫的作業。

範本程式庫，例如 ATL 不同於傳統的 c + + 類別庫，因為它們通常會提供僅作為來源的程式碼 （或加上一些支援執行的階段的原始碼），並不是原本就或一定是階層式本質。 而不是衍生自類別，以取得您想要的功能，您具現化範本的類別。

## <a name="see-also"></a>另請參閱

[ATL 簡介](../atl/introduction-to-atl.md)

