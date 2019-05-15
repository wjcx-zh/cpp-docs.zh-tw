---
title: 編譯器警告 (層級 1) C4743
ms.date: 05/13/2019
f1_keywords:
- C4743
helpviewer_keywords:
- C4743
ms.assetid: 2ee76ea3-77f3-4c2f-9a57-0751823c89fd
ms.openlocfilehash: 53ead0e34b55eca44399cee09f1947a12e1eadd3
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611839"
---
# <a name="compiler-warning-level-1-c4743"></a>編譯器警告 (層級 1) C4743

'*型別*'有不同的大小'*file1*'和'*file2*':*數目*並*數目*位元組

外部變數參考，或在兩個檔案中定義具有這些檔案中，不同的類型，編譯器已判斷中變數的大小*file1*中的變數大小不同*file2*.

## <a name="remarks"></a>備註

沒有的重要案例時可以發出這個警告，如C++。 如果您宣告具有相同名稱在兩個不同的檔案相同的類型，如果這些宣告包含虛擬函式，而且如果宣告不是相同，編譯器可發出警告 C4744 虛擬函式的資料表。 有兩個不同大小的虛擬函式做為相同的類型，和連結器必須選擇其中一個，將合併到可執行檔，就會發生此警告。  可以，它可能會導致您的程式錯誤的虛擬函式的呼叫。

若要解決這個警告，使用相同的型別定義，或使用不同的類型或變數的名稱。

## <a name="example"></a>範例

下列範例會產生 C4743。 若要編譯它，將這兩個檔案放在相同的資料夾，然後再執行  

```cmd
cl /EHsc /W1 /GL /O2 C4743a.cpp C4743b.cpp
```

```cpp
// C4743a.cpp
class C {
public:
    virtual void f1(void);
    virtual void f2(void);
    virtual void f3(void);
};

void C::f1(void) {}
void C::f2(void) {}
void C::f3(void) {}
C q;
```

```cpp
// C4743b.cpp
class C {
public:
    virtual void f1(void);
    virtual void f2(void);
    virtual void f3(void);
    virtual void f4(void);
    virtual void f5(void);
};

void C::f4(void) {}
void C::f5(void) {}
C x;

int main() {}
```
