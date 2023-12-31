# 写题的算法

[interesting_Web](https://giancarlo-ma.github.io/categories/CS61A/)



python逻辑判断：
``or``\``and`` ``isnot``
``&  with | `` 成了位运算。



## Recusion
[code](./homework/hw02/hw02.py)
basic case 可以很“复杂”.计算机仅保证你这么思考，会得到这样的结果。

重要的：观察父子递归中间的关系，甚至可以创造参数通过记录关系通关

**Towers of Hanoi**
```python
def move_disk(disk_number, form_peg, to_peg):
    print("Move disk" + str(disk_number)+"from peg" + str(from_peg)+ "to peg" + str(to_peg)+".")


def solve_hanoi(n,start_peg, end_peg):
    if n == 1:
        move_disk(n, start_peg, end_peg)
    else:
        spare_peg = 6 - start_peg -end_peg
        solve_hanoi(n-1, start_peg, spare_peg)
```



**count_partitions**

```python
def count_coins(total):
    """Return the number of ways to make change for total using coins of value of 1, 5, 10, 25.
    >>> count_coins(15)
    6
    >>> count_coins(10)
    4
    >>> count_coins(20)
    9
    >>> count_coins(100) # How many ways to make change for a dollar?
    242
    >>> from construct_check import check
    >>> # ban iteration
    >>> check(HW_SOURCE_FILE, 'count_coins', ['While', 'For'])                                          
    True
    """
    "*** YOUR CODE HERE ***"
    def help_count(num,coin=1):
        next_coin=next_largest_coin(coin)
        if coin == 25 :
            next_coin=25
        if num == 0:
            return 1
        elif num < 0:
            return 0
        elif coin == 25:
            return help_count(num-coin,coin)
        else:
            return help_count(num-coin,coin)+help_count(num,next_coin)
    return help_count(total,1)

```

base case!!! Single line thinking __pay attention to the special cases