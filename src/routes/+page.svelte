<script lang="ts">
	import katex from 'katex';

	type ElementType = { z: number; elecneg: number; type: string };

	const elements: { [key: string]: ElementType } = {
		H: { z: 1, elecneg: 2.2, type: 'nonmetal' },
		He: { z: 2, elecneg: -1, type: 'noblegas' },
		Li: { z: 3, elecneg: 0.98, type: 'metal' },
		Be: { z: 4, elecneg: 1.57, type: 'metal' },
		B: { z: 5, elecneg: 2.04, type: 'nonmetal' },
		C: { z: 6, elecneg: 2.55, type: 'nonmetal' },
		N: { z: 7, elecneg: 3.04, type: 'nonmetal' },
		O: { z: 8, elecneg: 3.44, type: 'nonmetal' },
		F: { z: 9, elecneg: 3.98, type: 'nonmetal' },
		Ne: { z: 10, elecneg: -1, type: 'noblegas' },
		Na: { z: 11, elecneg: 0.93, type: 'metal' },
		Mg: { z: 12, elecneg: 1.31, type: 'metal' },
		Al: { z: 13, elecneg: 1.61, type: 'metal' },
		Si: { z: 14, elecneg: 1.9, type: 'nonmetal' },
		P: { z: 15, elecneg: 2.19, type: 'nonmetal' },
		S: { z: 16, elecneg: 2.58, type: 'nonmetal' },
		Cl: { z: 17, elecneg: 3.16, type: 'nonmetal' },
		Ar: { z: 18, elecneg: -1, type: 'noblegas' },
		K: { z: 19, elecneg: 0.82, type: 'metal' },
		Ca: { z: 20, elecneg: 1.0, type: 'metal' },
		Sc: { z: 21, elecneg: 1.36, type: 'metal' },
		Ti: { z: 22, elecneg: 1.54, type: 'metal' },
		V: { z: 23, elecneg: 1.63, type: 'metal' },
		Cr: { z: 24, elecneg: 1.66, type: 'metal' },
		Mn: { z: 25, elecneg: 1.55, type: 'metal' },
		Fe: { z: 26, elecneg: 1.83, type: 'metal' },
		Co: { z: 27, elecneg: 1.88, type: 'metal' },
		Ni: { z: 28, elecneg: 1.91, type: 'metal' },
		Cu: { z: 29, elecneg: 1.9, type: 'metal' },
		Zn: { z: 30, elecneg: 1.65, type: 'metal' },
		Ga: { z: 31, elecneg: 1.81, type: 'metal' },
		Ge: { z: 32, elecneg: 2.01, type: 'metal' },
		As: { z: 33, elecneg: 2.18, type: 'nonmetal' },
		Se: { z: 34, elecneg: 2.55, type: 'nonmetal' },
		Br: { z: 35, elecneg: 2.96, type: 'nonmetal' },
		Kr: { z: 36, elecneg: 3.0, type: 'noblegas' },
		Rb: { z: 37, elecneg: 0.82, type: 'metal' },
		Sr: { z: 38, elecneg: 0.95, type: 'metal' },
		Y: { z: 39, elecneg: 1.22, type: 'metal' },
		Zr: { z: 40, elecneg: 1.33, type: 'metal' },
		Nb: { z: 41, elecneg: 1.6, type: 'metal' },
		Mo: { z: 42, elecneg: 2.16, type: 'metal' },
		Tc: { z: 43, elecneg: 1.9, type: 'metal' },
		Ru: { z: 44, elecneg: 2.2, type: 'metal' },
		Rh: { z: 45, elecneg: 2.28, type: 'metal' },
		Pd: { z: 46, elecneg: 2.2, type: 'metal' },
		Ag: { z: 47, elecneg: 1.93, type: 'metal' },
		Cd: { z: 48, elecneg: 1.69, type: 'metal' },
		In: { z: 49, elecneg: 1.78, type: 'metal' },
		Sn: { z: 50, elecneg: 1.96, type: 'metal' },
		Sb: { z: 51, elecneg: 2.05, type: 'metal' },
		Te: { z: 52, elecneg: 2.1, type: 'nonmetal' },
		I: { z: 53, elecneg: 2.66, type: 'nonmetal' },
		Xe: { z: 54, elecneg: 2.6, type: 'noblegas' },
		Cs: { z: 55, elecneg: 0.79, type: 'metal' },
		Ba: { z: 56, elecneg: 0.89, type: 'metal' },
		La: { z: 57, elecneg: 1.1, type: 'metal' },
		Ce: { z: 58, elecneg: 1.12, type: 'metal' },
		Pr: { z: 59, elecneg: 1.13, type: 'metal' },
		Nd: { z: 60, elecneg: 1.14, type: 'metal' },
		Pm: { z: 61, elecneg: 1.13, type: 'metal' },
		Sm: { z: 62, elecneg: 1.17, type: 'metal' },
		Eu: { z: 63, elecneg: 1.2, type: 'metal' },
		Gd: { z: 64, elecneg: 1.2, type: 'metal' },
		Tb: { z: 65, elecneg: 1.1, type: 'metal' },
		Dy: { z: 66, elecneg: 1.22, type: 'metal' },
		Ho: { z: 67, elecneg: 1.23, type: 'metal' },
		Er: { z: 68, elecneg: 1.24, type: 'metal' },
		Tm: { z: 69, elecneg: 1.25, type: 'metal' },
		Yb: { z: 70, elecneg: 1.1, type: 'metal' },
		Lu: { z: 71, elecneg: 1.27, type: 'metal' },
		Hf: { z: 72, elecneg: 1.3, type: 'metal' },
		Ta: { z: 73, elecneg: 1.5, type: 'metal' },
		W: { z: 74, elecneg: 2.36, type: 'metal' },
		Re: { z: 75, elecneg: 1.9, type: 'metal' },
		Os: { z: 76, elecneg: 2.2, type: 'metal' },
		Ir: { z: 77, elecneg: 2.2, type: 'metal' },
		Pt: { z: 78, elecneg: 2.28, type: 'metal' },
		Au: { z: 79, elecneg: 2.54, type: 'metal' },
		Hg: { z: 80, elecneg: 2.0, type: 'metal' },
		Tl: { z: 81, elecneg: 1.62, type: 'metal' },
		Pb: { z: 82, elecneg: 2.33, type: 'metal' },
		Bi: { z: 83, elecneg: 2.02, type: 'metal' },
		Po: { z: 84, elecneg: 2.0, type: 'metal' },
		At: { z: 85, elecneg: 2.2, type: 'nonmetal' },
		Rn: { z: 86, elecneg: -1, type: 'noblegas' },
		Fr: { z: 87, elecneg: 0.7, type: 'metal' },
		Ra: { z: 88, elecneg: 0.9, type: 'metal' },
		Ac: { z: 89, elecneg: 1.1, type: 'metal' },
		Th: { z: 90, elecneg: 1.3, type: 'metal' },
		Pa: { z: 91, elecneg: 1.5, type: 'metal' },
		U: { z: 92, elecneg: 1.38, type: 'metal' },
		Np: { z: 93, elecneg: 1.36, type: 'metal' },
		Pu: { z: 94, elecneg: 1.28, type: 'metal' },
		Am: { z: 95, elecneg: 1.3, type: 'metal' },
		Cm: { z: 96, elecneg: 1.3, type: 'metal' },
		Bk: { z: 97, elecneg: 1.3, type: 'metal' },
		Cf: { z: 98, elecneg: 1.3, type: 'metal' },
		Es: { z: 99, elecneg: 1.3, type: 'metal' },
		Fm: { z: 100, elecneg: -1, type: 'metal' },
		Md: { z: 101, elecneg: -1, type: 'metal' },
		No: { z: 102, elecneg: -1, type: 'metal' },
		Lr: { z: 103, elecneg: -1, type: 'metal' },
		Rf: { z: 104, elecneg: -1, type: '' },
		Db: { z: 105, elecneg: -1, type: '' },
		Sg: { z: 106, elecneg: -1, type: '' },
		Bh: { z: 107, elecneg: -1, type: '' },
		Hs: { z: 108, elecneg: -1, type: '' },
		Mt: { z: 109, elecneg: -1, type: '' },
		Ds: { z: 110, elecneg: -1, type: '' },
		Rg: { z: 111, elecneg: -1, type: '' },
		Cn: { z: 112, elecneg: -1, type: '' },
		Nh: { z: 113, elecneg: -1, type: '' },
		Fl: { z: 114, elecneg: -1, type: '' },
		Mc: { z: 115, elecneg: -1, type: '' },
		Lv: { z: 116, elecneg: -1, type: '' },
		Ts: { z: 117, elecneg: -1, type: '' },
		Og: { z: 118, elecneg: -1, type: '' }
	};

	let firstNucleus: string;
	let secondNucleus: string;
	function calculate() {
		const firstElement: ElementType = elements[firstNucleus];
		const secondElement: ElementType = elements[secondNucleus];
		const electronegativitySubtraction = Math.abs(firstElement.elecneg - secondElement.elecneg);

		let calculated: {
			firstElementName: string;
			firstElement: ElementType;
			secondElementName: string;
			secondElement: ElementType;
			electronegativitySubtraction: number;
			bondType: string;
		} = {
			firstElementName: firstNucleus,
			firstElement: firstElement,
			secondElementName: secondNucleus,
			secondElement: secondElement,
			electronegativitySubtraction: electronegativitySubtraction,
			bondType: ''
		};

		if (0 <= electronegativitySubtraction && electronegativitySubtraction < 0.4)
			calculated.bondType = 'cộng hóa trị không cực';
		else if (0.4 <= electronegativitySubtraction && electronegativitySubtraction < 1.7)
			calculated.bondType = 'cộng hóa trị có cực';
		else if (electronegativitySubtraction >= 1.7) {
			if (firstElement.type == 'nonmetal' && secondElement.type == 'nonmetal')
				calculated.bondType = 'cộng hóa trị có cực';
			else calculated.bondType = 'ion';
		}
		return calculated;
	}

	let answer: {
		firstElementName: string;
		firstElement: ElementType;
		secondElementName: string;
		secondElement: ElementType;
		electronegativitySubtraction: number;
		bondType: string;
	};
</script>

<svelte:head>
	<title>Tính hiệu độ âm điện của 2 nguyên tử</title>
	<link
		rel="stylesheet"
		href="https://cdn.jsdelivr.net/npm/katex@0.12.0/dist/katex.min.css"
		integrity="sha384-AfEj0r4/OFrOo5t7NnNe46zW/tFgW6x/bCJG8FqQCEo3+Aro6EYUG4+cU+KJWu/X"
		crossorigin="anonymous"
	/>
</svelte:head>

<div>
	<div class="fixed left-1/2 top-10 w-1/2 -translate-x-1/2 space-y-4">
		<label class="input input-lg input-bordered flex items-center gap-2">
			Nguyên tử thứ nhất
			<input type="text" class="grow" placeholder="Na" bind:value={firstNucleus} />
		</label>
		<label class="input input-lg input-bordered flex items-center gap-2">
			Nguyên tử thứ hai
			<input type="text" class="grow" placeholder="Cl" bind:value={secondNucleus} />
		</label>
		<button
			class="btn btn-primary w-full"
			onclick={() => {
				answer = calculate();
				firstNucleus = '';
				secondNucleus = '';
			}}>Tính</button
		>
	</div>

	{#if answer}
		<div class="fixed left-10 top-80 text-4xl">
			<h1>
				Hiệu độ âm điện của {answer.firstElementName} và {answer.secondElementName} là:
			</h1>
			{@html katex.renderToString(
				`\\Delta\\chi_{${answer.firstElementName}-${answer.secondElementName}}=|\\chi _{${answer.firstElementName}}-\\chi_{${answer.secondElementName}}|=|${answer.firstElement.elecneg}-${answer.secondElement.elecneg}|=${answer.electronegativitySubtraction.toFixed(2)}`,
				{
					displayMode: false,
					throwOnError: false
				}
			)}
			<h2>Loại liên kết: Liên kết {answer.bondType}</h2>
		</div>
	{/if}
</div>
