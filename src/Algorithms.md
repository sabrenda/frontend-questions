<div align="center"><h1>Алгоритмы</h1></div>

[⚙️ Back to menu](../README.md)

 <div id="menu"></div>

| No.|             Вопрос                   |
|:---|:-------------------------------------|
|1| [Виды сортировки](#a1)|


---

<div id="a1"></div>

## 1. Виды сортировки

### Сортировка пузырьком

Концепция сортировки пузырьком заключается в сравнении и последовательном обмене соседних элементов массива до тех пор, пока массив не будет отсортирован по возрастанию или убыванию.

```jsx
function bubbleSort(arr) {
	let len = arr.length;
	for (let i = 0; i < len; i++) {
		for (let j = 0; j < len - 1; j++) {
			if (arr[j] > arr[j + 1]) {
				let temp = arr[j];
				arr[j] = arr[j + 1];
				arr[j + 1] = temp;
			}
		}
	}
	return arr;
}

let array = [5, 3, 8, 4, 2];
console.log(bubbleSort(array)); // Output: [2, 3, 4, 5, 8]
```
### Сортировка выбором

Сортировка выбором находит минимальный (или максимальный) элемент и перемещает его в начало (или конец) массива, повторяя этот процесс для оставшихся элементов.

```jsx
function selectionSort(arr) {
	let len = arr.length;
	for (let i = 0; i < len - 1; i++) {
		let minIndex = i;
		for (let j = i + 1; j < len; j++) {
			if (arr[j] < arr[minIndex]) {
				minIndex = j;
			}
		}
		if (minIndex !== i) {
			let temp = arr[i];
			arr[i] = arr[minIndex];
			arr[minIndex] = temp;
		}
	}
	return arr;
}

let array = [5, 3, 8, 4, 2];
console.log(selectionSort(array)); // Output: [2, 3, 4, 5, 8]
```

### Сортировка вставками

Сортировка вставками строит отсортированную часть массива по одному элементу за раз, вставляя каждый следующий элемент в правильную позицию относительно предыдущих элементов.

```jsx
function insertionSort(arr) {
	let len = arr.length;
	for (let i = 1; i < len; i++) {
		let key = arr[i];
		let j = i - 1;
		while (j >= 0 && arr[j] > key) {
			arr[j + 1] = arr[j];
			j--;
		}
		arr[j + 1] = key;
	}
	return arr;
}

let array = [5, 3, 8, 4, 2];
console.log(insertionSort(array)); // Output: [2, 3, 4, 5, 8]
```

### Сортировка слиянием

Сортировка слиянием разделяет массив на половины, рекурсивно сортирует каждую половину, а затем объединяет две отсортированные половины в одну.    

```jsx
function mergeSort(arr) {
	if (arr.length <= 1) {
		return arr;
	}
	
	const middle = Math.floor(arr.length / 2);
	const left = arr.slice(0, middle);
	const right = arr.slice(middle);
	
	return merge(mergeSort(left), mergeSort(right));
}

function merge(left, right) {
	let result = [];
	let leftIndex = 0;
	let rightIndex = 0;

	while (leftIndex < left.length && rightIndex < right.length) {
		if (left[leftIndex] < right[rightIndex]) {
			result.push(left[leftIndex]);
			leftIndex++;
		} else {
			result.push(right[rightIndex]);
			rightIndex++;
		}
	}

	return result.concat(left.slice(leftIndex)).concat(right.slice(rightIndex));
}

let array = [5, 3, 8, 4, 2];
console.log(mergeSort(array)); // Output: [2, 3, 4, 5, 8]
```

### Быстрая сортировка

Быстрая сортировка использует метод "разделяй и властвуй", выбирая опорный элемент, разбивая массив на две части: элементы, меньшие опорного, и элементы, большие опорного, затем рекурсивно сортирует каждую из этих частей.

```jsx
function quickSort(arr) {
	if (arr.length <= 1) {
		return arr;
	}

	const pivot = arr[arr.length - 1];
	const left = [];
	const right = [];

	for (let i = 0; i < arr.length - 1; i++) {
		if (arr[i] < pivot) {
			left.push(arr[i]);
		} else {
			right.push(arr[i]);
		}
	}

	return [...quickSort(left), pivot, ...quickSort(right)];
}

let array = [5, 3, 8, 4, 2];
console.log(quickSort(array)); // Output: [2, 3, 4, 5, 8]
```

### Блочная сортировка

Блочная сортировка разбивает массив на равные интервалы (или блоки), сортирует каждый блок и затем объединяет отсортированные блоки в итоговый отсортированный массив.

```jsx
function bucketSort(arr, bucketSize = 5) {
	if (arr.length === 0) {
		return arr;
	}

	const min = Math.min(...arr);
	const max = Math.max(...arr);
	const bucketCount = Math.floor((max - min) / bucketSize) + 1;
	const buckets = new Array(bucketCount);

	for (let i = 0; i < buckets.length; i++) {
		buckets[i] = [];
	}

	for (let i = 0; i < arr.length; i++) {
		const bucketIndex = Math.floor((arr[i] - min) / bucketSize);
		buckets[bucketIndex].push(arr[i]);
	}

	arr.length = 0;

	for (let i = 0; i < buckets.length; i++) {
		insertionSort(buckets[i]);
		arr.push(...buckets[i]);
	}

	return arr;
}

let array = [5, 3, 8, 4, 2];
console.log(bucketSort(array)); // Output: [2, 3, 4, 5, 8]
```

[Оглавление - Задачи 🔼](#menu)
