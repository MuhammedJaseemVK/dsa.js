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
console.log(minEatingSpeed(piles, h);
```
Time Complexity:  max(piles) * N

Space Complexity:  O(1)
