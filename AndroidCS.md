# Andorid CS 정리

## Fragment의 lifecycleOwner로 this, viewLifecycleOwner의 차이
lifecycleOwner는 Fragment의 전반적인 생명주기를 뜻한다. `onAttach ~ onDestroy`까지 포함한다.
viewLifecycleOwner는 프래그먼트 뷰의 생명주기를 가진다. `onCreateView ~ onDestroyView`까지를 포함하낟.
기존의 프래그먼트는 하나의 lifecycle을 가지고 있다. 하지만 프래그먼트는 액티비티와 달리 `onDestroy`가 호출하지 않은 상태에서 `onCreateView`가 여러번 호출 될 수 있다.

만약 `A Fragment`에서 `B Fragment`로 이동할 때 `A Fragment`의 `onDestroyView`는 호출되지만 `onDestroy`는 호출되지 않기에
뷰는 파괴되지만 프래그먼트 자체는 남아있는 상태다. 이런 경우 메모리 누수가 발생할 수 있다.