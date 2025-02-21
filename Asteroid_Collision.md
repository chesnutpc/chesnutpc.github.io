---
layout: default
title: Asteroid Collision
---

## Asteroid Collision

### Question
You are given an array of asteroids represented by integers.  Negative intergers indicate that they are moving to the left, positive that they are moving to the right.  All asteroids move at the same speed.  When two asteroids collide, the smaller asteroid explodes leaving the larger asteroid.  If two asteroids of the same size collide, both asteroids explode.  Write a function that takes in an array of asteroids and returns an array of asteroids after all collisions.

Sample Input:
asteroids = [-2, 5, -9, 5, 7, -3, -7]

Sample Output:
[-2, -9, 5]

Explanation:
The -9 collides with the 5, destroying the 5.\
The 7 collides with the -3, destroying the -3.\
The 7 collides with the -7, both get destroyed.

### Solution
```
def collidingAsteroids(asteroids):
    resultStack = []
    for asteroid in asteroids:
        # if an asteroid is moving right, it will never collide with any 
        # previous asteroid in the stack, simply add it to the stack
        if asteroid > 0:
            resultStack.append(asteroid)
            continue # move on to the next asteroid
        # if an asteroid is moving left, check if the asteroid on the top
        # of the stack is moving right, evaluate the collision
        while True:
            # if the asteroid at the top is moving left or there are no
            # asteroids, there will be no collisions, simply add it to
            # the stack
            if len(resultStack) == 0 or resultStack[-1] < 0:
                resultStack.append(asteroid)
                break # no more collisions
            
            # there will be a collision, so we need to compare asteroids
            asteroidSize = abs(asteroid)
            # this asteroid is smaller than the asteroid in the stack
            # do nothing because a collision will break this asteroid
            if resultStack[-1] > asteroidSize:
                break
            # this asteroid is the same size as the asteroid on top of
            # the stack, pop the stack as the collision will destroy
            # both asteroids
            if resultStack[-1] == asteroidSize:
                resultStack.pop()
                break
            # this asteroid must be bigger than the asteroid on top of the 
            # stack, pop the stack to remove the asteroid
            resultStack.pop()
            # now continue through the while loop, this asteroid will
            # either get appended to the stack or have another collision
            
    return resultStack
```
O(n) space due to the need to create a return list\
O(n) time because the inputted list must be iterated through.
