---
description: "Learn more about: CPoint Class"
title: "CPoint Class"
ms.date: "11/04/2016"
f1_keywords: ["CPoint", "ATLTYPES/ATL::CPoint", "ATLTYPES/ATL::CPoint::CPoint", "ATLTYPES/ATL::CPoint::Offset"]
helpviewer_keywords: ["LPPOINT structure", "POINT structure", "CPoint class"]
---
# `CPoint` Class

Similar to the Windows `POINT` structure.

## Syntax

```
class CPoint : public tagPOINT
```

## Members

### Public Constructors

|Name|Description|
|----------|-----------------|
|[`CPoint::CPoint`](#cpoint)|Constructs a `CPoint`.|

### Public Methods

|Name|Description|
|----------|-----------------|
|[`CPoint::Offset`](#offset)|Adds values to the `x` and `y` members of the `CPoint`.|

### Public Operators

|Name|Description|
|----------|-----------------|
|[`CPoint::operator -`](#operator_-)|Returns the difference of a `CPoint` and a `SIZE`, or the negation of a `POINT`, or the `CSize` difference between two `POINT`s, or the offset by a negative `SIZE`.|
|[`CPoint::operator !=`](#operator_neq)|Checks for inequality between two `POINT`s.|
|[`CPoint::operator +`](#operator_add)|Returns the sum of a `CPoint` and a `SIZE` or `POINT`, or a `CRect` offset by a `SIZE`.|
|[`CPoint::operator +=`](#operator_add_eq)|Offsets `CPoint` by adding a `SIZE` or `POINT`.|
|[`CPoint::operator -=`](#operator_-_eq)|Offsets `CPoint` by subtracting a `SIZE` or `POINT`.|
|[`CPoint::operator ==`](#operator_eq_eq)|Checks for equality between two `POINT`s.|

## Remarks

It also includes member functions to manipulate `CPoint` and [`POINT`](/windows/win32/api/windef/ns-windef-point) structures.

A `CPoint` object can be used wherever a `POINT` structure is used. The operators of this class that interact with a `SIZE` accept either [`CSize`](../../atl-mfc-shared/reference/csize-class.md) objects or [`SIZE`](/windows/win32/api/windef/ns-windef-size) structures, since the two are interchangeable.

> [!NOTE]
> This class is derived from the `tagPOINT` structure. (The name `tagPOINT` is a less commonly used name for the `POINT` structure.) This means that the data members of the `POINT` structure, `x` and `y`, are accessible data members of `CPoint`.

> [!NOTE]
> For more information on shared utility classes (like `CPoint`), see [Shared Classes](../../atl-mfc-shared/atl-mfc-shared-classes.md).

## Inheritance Hierarchy

`tagPOINT`

`CPoint`

## Requirements

**Header:** `atltypes.h`

## <a name="cpoint"></a> `CPoint::CPoint`

Constructs a `CPoint` object.

```
CPoint() throw();
CPoint(int initX, int initY) throw();
CPoint(POINT initPt) throw();
CPoint(SIZE initSize) throw();
CPoint(LPARAM dwPoint) throw();
```

### Parameters

*`initX`*\
Specifies the value of the `x` member of `CPoint`.

*`initY`*\
Specifies the value of the `y` member of `CPoint`.

*`initPt`*\
[`POINT`](/windows/win32/api/windef/ns-windef-point) structure or `CPoint` that specifies the values used to initialize `CPoint`.

*`initSize`*\
[`SIZE`](/windows/win32/api/windef/ns-windef-size) structure or [`CSize`](../../atl-mfc-shared/reference/csize-class.md) that specifies the values used to initialize `CPoint`.

*`dwPoint`*\
Sets the `x` member to the low-order word of *`dwPoint`* and the `y` member to the high-order word of *`dwPoint`*.

### Remarks

If no arguments are given, `x` and `y` members are set to 0.

### Example

```cpp
CPoint   ptTopLeft(0, 0);
// works from a POINT, too

POINT   ptHere;
ptHere.x = 35;
ptHere.y = 95;

CPoint   ptMFCHere(ptHere);

// works from a SIZE
SIZE   sHowBig;
sHowBig.cx = 300;
sHowBig.cy = 10;

CPoint ptMFCBig(sHowBig);
// or from a DWORD

DWORD   dwSize;
dwSize = MAKELONG(35, 95);

CPoint ptFromDouble(dwSize);
ASSERT(ptFromDouble == ptMFCHere);
```

## <a name="offset"></a> `CPoint::Offset`

Adds values to the `x` and `y` members of the `CPoint`.

```cpp
void Offset(int xOffset, int yOffset) throw();
void Offset(POINT point) throw();
void Offset(SIZE size) throw();
```

### Parameters

*`xOffset`*\
Specifies the amount to offset the `x` member of the `CPoint`.

*`yOffset`*\
Specifies the amount to offset the `y` member of the `CPoint`.

*`point`*\
Specifies the amount ([`POINT`](/windows/win32/api/windef/ns-windef-point) or `CPoint`) to offset the `CPoint`.

*`size`*\
Specifies the amount ([`SIZE`](/windows/win32/api/windef/ns-windef-size) or [`CSize`](../../atl-mfc-shared/reference/csize-class.md)) to offset the `CPoint`.

### Example

[!code-cpp[NVC_ATLMFC_Utilities#28](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_1.cpp)]

## <a name="operator_eq_eq"></a> `CPoint::operator ==`

Checks for equality between two `POINT`s.

```
BOOL operator==(POINT point) const throw();
```

### Parameters

*`point`*\
Contains a [`POINT`](/windows/win32/api/windef/ns-windef-point) structure or `CPoint` object.

### Return Value

Nonzero if the `POINT`s are equal; otherwise 0.

### Example

[!code-cpp[NVC_ATLMFC_Utilities#29](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_2.cpp)]

## <a name="operator_neq"></a> `CPoint::operator !=`

Checks for inequality between two `POINT`s.

```
BOOL operator!=(POINT point) const throw();
```

### Parameters

*`point`*\
Contains a [`POINT`](/windows/win32/api/windef/ns-windef-point) structure or `CPoint` object.

### Return Value

Nonzero if the `POINT`s aren't equal; otherwise 0.

### Example

[!code-cpp[NVC_ATLMFC_Utilities#30](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_3.cpp)]

## <a name="operator_add_eq"></a> `CPoint::operator +=`

The first overload adds a `SIZE` to the `CPoint`.

```cpp
void operator+=(SIZE size) throw();
void operator+=(POINT point) throw();
```

### Parameters

*`size`*\
Contains a [`SIZE`](/windows/win32/api/windef/ns-windef-size) structure or [`CSize`](../../atl-mfc-shared/reference/csize-class.md) object.

*`point`*\
Contains a [`POINT`](/windows/win32/api/windef/ns-windef-point) structure or [`CPoint`](../../atl-mfc-shared/reference/cpoint-class.md) object.

### Remarks

The second overload adds a `POINT` to the `CPoint`.

In both cases, addition is done by adding the `x` (or `cx`) member of the right-hand operand to the `x` member of the `CPoint` and adding the `y` (or `cy`) member of the right-hand operand to the `y` member of the `CPoint`.

For example, adding `CPoint(5, -7)` to a variable that contains `CPoint(30, 40)` changes the variable to `CPoint(35, 33)`.

### Example

[!code-cpp[NVC_ATLMFC_Utilities#31](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_4.cpp)]

## <a name="operator_-_eq"></a> `CPoint::operator -=`

The first overload subtracts a `SIZE` from the `CPoint`.

```cpp
void operator-=(SIZE size) throw();
void operator-=(POINT point) throw();
```

### Parameters

*`size`*\
Contains a [`SIZE`](/windows/win32/api/windef/ns-windef-size) structure or [`CSize`](../../atl-mfc-shared/reference/csize-class.md) object.

*`point`*\
Contains a [`POINT`](/windows/win32/api/windef/ns-windef-point) structure or [`CPoint`](../../atl-mfc-shared/reference/cpoint-class.md) object.

### Remarks

The second overload subtracts a `POINT` from the `CPoint`.

In both cases, subtraction is done by subtracting the `x` (or `cx`) member of the right-hand operand from the `x` member of the `CPoint` and subtracting the `y` (or `cy`) member of the right-hand operand from the `y` member of the `CPoint`.

For example, subtracting `CPoint(5, -7)` from a variable that contains `CPoint(30, 40)` changes the variable to `CPoint(25, 47)`.

### Example

[!code-cpp[NVC_ATLMFC_Utilities#32](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_5.cpp)]

## <a name="operator_add"></a> `CPoint::operator +`

Use this operator to offset `CPoint` by a `CPoint` or `CSize` object, or to offset a `CRect` by a `CPoint`.

```
CPoint operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw();
```

### Parameters

*`size`*\
Contains a [`SIZE`](/windows/win32/api/windef/ns-windef-size) structure or [`CSize`](../../atl-mfc-shared/reference/csize-class.md) object.

*`point`*\
Contains a [`POINT`](/windows/win32/api/windef/ns-windef-point) structure or [`CPoint`](../../atl-mfc-shared/reference/cpoint-class.md) object.

*`lpRect`*\
Contains a pointer to a [`RECT`](/windows/win32/api/windef/ns-windef-rect) structure or [`CRect`](../../atl-mfc-shared/reference/crect-class.md) object.

### Return Value

A `CPoint` that is offset by a `SIZE`, a `CPoint` that is offset by a `POINT`, or a `CRect` offset by a `POINT`.

### Remarks

For example, using one of the first two overloads to offset the point `CPoint(25, -19)` by a point `CPoint(15, 5)` or size `CSize(15, 5)` returns the value `CPoint(40, -14)`.

Adding a `CRect` to a `POINT` returns the `CRect` after being offset by the `x` and `y` values specified in the `POINT`. For example, using the last overload to offset a rectangle `CRect(125, 219, 325, 419)` by a point `CPoint(25, -19)` returns `CRect(150, 200, 350, 400)`.

### Example

[!code-cpp[NVC_ATLMFC_Utilities#33](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_6.cpp)]

## <a name="operator_-"></a> `CPoint::operator -`

Use one of the first two overloads to subtract a `CPoint` or `CSize` object from `CPoint`.

```
CSize operator-(POINT point) const throw();
CPoint operator-(SIZE size) const throw();
CRect operator-(const RECT* lpRect) const throw();
CPoint operator-() const throw();
```

### Parameters

*`point`*\
A [`POINT`](/windows/win32/api/windef/ns-windef-point) structure or [`CPoint`](../../atl-mfc-shared/reference/cpoint-class.md) object.

*`size`*\
A [`SIZE`](/windows/win32/api/windef/ns-windef-size) structure or [`CSize`](../../atl-mfc-shared/reference/csize-class.md) object.

*`lpRect`*\
A pointer to a [`RECT`](/windows/win32/api/windef/ns-windef-rect) structure or a [`CRect`](../../atl-mfc-shared/reference/crect-class.md) object.

### Return Value

A `CSize` that is the difference between two `POINT`s, a `CPoint` that is offset by the negation of a `SIZE`, a `CRect` that is offset by the negation of a `POINT`, or a `CPoint` that is the negation of a `POINT`.

### Remarks

The third overload offsets a `CRect` by the negation of `CPoint`. Finally, use the unary operator to negate `CPoint`.

For example, using the first overload to find the difference between two points `CPoint(25, -19)` and `CPoint(15, 5)` returns `CSize(10, -24)`.

Subtracting a `CSize` from `CPoint` does the same calculation as above but returns a `CPoint` object, not a `CSize` object. For example, using the second overload to find the difference between the point `CPoint(25, -19)` and the size `CSize(15, 5)` returns `CPoint(10, -24)`.

Subtracting a rectangle from a `POINT` returns the rectangle offset by the negatives of the `x` and `y` values specified in the `POINT`. For example, using the last overload to offset the rectangle `CRect(125, 200, 325, 400)` by the point `CPoint(25, -19)` returns `CRect(100, 219, 300, 419)`.

Use the unary operator to negate a `POINT`. For example, using the unary operator with the point `CPoint(25, -19)` returns `CPoint(-25, 19)`.

### Example

[!code-cpp[NVC_ATLMFC_Utilities#34](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_7.cpp)]

## See also

[MFC Sample MDI](../../overview/visual-cpp-samples.md)\
[Hierarchy Chart](../../mfc/hierarchy-chart.md)\
[`POINT` Structure](/windows/win32/api/windef/ns-windef-point)\
[`CRect` Class](../../atl-mfc-shared/reference/crect-class.md)\
[`CSize` Class](../../atl-mfc-shared/reference/csize-class.md)
