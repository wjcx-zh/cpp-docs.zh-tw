---
title: 使用 Template Library (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- template libraries
ms.assetid: 5e80ec6e-a61c-41ce-b34b-9a6252c46265
ms.openlocfilehash: 7b1a6b0befcfd7ecf0a150653b5c32239b7f9543
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62195127"
---
# <a name="using-a-template-library"></a>使用範本程式庫

範本有些許類似巨集。 使用巨集，因為叫用範本會使它 （使用適當的參數替代） 依序展開您所撰寫的程式碼。 不過，樣板更進一步這可讓您當做參數傳遞的類型為基礎的新類別的建立。 這些新的類別會實作型別安全方式來執行您的範本程式碼所編寫的作業。

不同於傳統的範本程式庫，例如 ATLC++類別庫，它們通常提供僅作為來源的程式碼 （或執行階段加上一些支援的原始碼），並不是原本就或一定是階層式本質上。 而不是衍生自類別，以取得您想要的功能，您具現化範本的類別。

## <a name="see-also"></a>另請參閱

[ATL 簡介](../atl/introduction-to-atl.md)
