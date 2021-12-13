<script lang="ts">
import Operator from "./components/Operator.svelte";
import Screen from "./components/Screen.svelte";
import { rows } from "./misc/rows";

let calculation = '';
let result = 0;

const handleOperation = (operation: string) => (): void => {
	if (operation === "clear") {
		calculation = "";
		result = 0;
	} else if (operation === "=") {
		const calcEval = eval(calculation);
		if (isNaN(calcEval)) {
			result = 0;
		} else {
			result = calcEval;
			calculation = "";
		}
	} else if (isNaN(+operation)) {
		calculation = calculation + " " + operation + " ";
	} else {
		calculation = calculation + +operation;
	}
}
</script>

<main>
	<div class="calculator">
		<Screen calculation={calculation} result={result} />
		<div class="keyboard">
			{#each rows as row }
			<div class="row">
				{#each row as button}
					<Operator
						on:click={handleOperation(button.operation)}
						label={button.label}
						operation={button.operation}
					/>
				{/each}
			</div>
		{/each}
		</div>
	</div>
</main>

<style type="scss">
body,
html {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100%;
}

.calculator {
  width: 30em;
}

.keyboard {
  width: 100%;
  height: 100%;

  display: flex;
  flex-direction: column;
}

.row {
  display: flex;
  flex-direction: row;

  width: 30em;
}
</style>