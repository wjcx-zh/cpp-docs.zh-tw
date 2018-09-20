---
title: 建構函式初始設定順序的變更 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- constructors, C++
ms.assetid: 8892c38d-6bf7-4cf7-ac8f-15e052135a79
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: fd54e9810131f3ddfabe458c70ddef081568a9cd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46397685"
---
# <a name="changes-in-constructor-initialization-order"></a>建構函式初始設定順序的變更

類別建構函式的初始設定順序已從 Managed Extensions for c + + Visual c + +。

## <a name="comparison-of-constructor-initialization-order"></a>建構函式初始設定順序的比較

Managed Extensions for c + +，在建構函式初始設定發生順序如下：

1. 建構函式的基底類別中，如果有的話，會叫用。

1. 會評估該類別的初始化清單。

1. 執行類別建構函式的程式碼主體。

執行此順序會遵循相同的慣例，如同原生 c + + 程式設計。 新的 Visual c + + 語言都自有一套 CLR 類別的下列執行順序：

1. 會評估該類別的初始化清單。

1. 建構函式的基底類別中，如果有的話，會叫用。

1. 執行類別建構函式的程式碼主體。

請注意這項變更只適用於 CLR 類別;在 Visual c + + 中的原生類別仍然會遵循先前的慣例。 在這兩種情況下，這些規則都會向上串聯的某一特定類別的整個階層鏈結。

請考慮下列使用 Managed Extensions for c + + 的程式碼範例：

```
__gc class A
{
public:
   A() : _n(1)
   {
   }

protected:
   int _n;
};

__gc class B : public A
{
public:
   B() : _m(_n)
   {
   }
private:
   int _m;
};
```

上述建構函式初始設定順序規定，我們應該會看到下列順序執行時新的類別的執行個體`B`建構：

1. 基底類別的建構函式`A`叫用。 `_n`成員已初始化成`1`。

1. 類別的初始化清單`B`評估。 `_m`成員已初始化成`1`。

1. 類別的程式碼主體`B`執行。

現在，請考慮在新的 Visual c + + 語法的相同程式碼：

```
ref class A
{
public:
   A() : _n(1)
   {
   }

protected:
   int _n;
};

ref class B : A
{
public:
   B() : _m(_n)
   {
   }
private:
   int _m;
};
```

當新的執行順序類別的執行個體`B`底下的新建構的語法是：

1. 類別的初始化清單`B`評估。 `_m`成員已初始化成`0`(`0`是 未初始化的值`_m`類別成員)。

1. 基底類別的建構函式`A`叫用。 `_n`成員已初始化成`1`。

1. 類別的程式碼主體`B`執行。

請注意類似的語法會產生不同的結果，這些程式碼範例。 類別的建構函式`B`基底類別的值而定`A`初始化其成員。 不過，類別的建構函式`A`有尚未被叫用。 繼承的類別取決於基底類別建構函式中發生的記憶體或資源配置時，則這類相依性可能會特別危險。

## <a name="what-this-means-going-from-managed-extensions-for-c-to-visual-c-2010"></a>此意義從 Managed Extensions for c + + 移至 Visual c + + 2010年

在許多情況下類別建構函式的執行順序的變更應該是透明的程式設計人員因為基底類別有沒有繼承的類別行為的概念。 不過，因為這些程式碼範例所示，繼承類別的建構函式可能會大幅影響時的初始設定清單的值相依於基底類別成員。 當您將您的程式碼從 Managed Extensions for c + + 的新語法時，請考慮將這類建構移至類別建構函式主體執行都一定出現在最後。

## <a name="see-also"></a>另請參閱

[Managed 類型 (C + + /cli CL)](../dotnet/managed-types-cpp-cl.md)<br/>
[建構函式](../cpp/constructors-cpp.md)
