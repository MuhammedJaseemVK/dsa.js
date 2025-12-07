# Koko eating bananas

https://leetcode.com/problems/koko-eating-bananas/

## Bruteforce

```ts
function minEatingSpeed(piles: number[], h: number): number {
    const max = Math.max(...piles);

    function calculateHours(piles: number[], hourly: number):number {
        let hours = 0;
        for (const pile of piles) {
            hours += Math.ceil(pile / hourly);
        }
        return hours;
    }

    for (let k = 0; k <= max; k++) {
        const hours = calculateHours(piles,k);
        if(hours<=h){
            return k;
        }
    }
    return max;
};


const piles = [7, 15, 6, 3];
const h = 8;
console.log(minEatingSpeed(piles, h));
```
Time Complexity:  O( max(piles) * N )

Space Complexity:  O(1)

## Optimal

```ts
function minEatingSpeed(piles: number[], h: number): number {
    let left = 1;
    let max = Math.max(...piles);
    let right = max;

    let answer = max;

    function calculateHours(piles: number[], hourly: number): number {
        let hours = 0;
        for (const pile of piles) {
            hours += Math.ceil(pile / hourly);
        }
        return hours;
    }

    while (left <= right) {
        const k = Math.floor((left + right) / 2);
        const hours = calculateHours(piles, k);
        if (hours <= h) {
            answer = k;
            right = k - 1;
        } else {
            left = k + 1;
        }
    }
    return answer;
};


const piles = [7, 15, 6, 3];
const h = 8;
console.log(minEatingSpeed(piles, h));
```
Time Complexity:  O ( log(max(piles)) * N )

Space Complexity:  O(1)
