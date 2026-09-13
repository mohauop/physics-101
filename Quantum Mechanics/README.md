# 🌟 Welcome to the Quantum Realm: From Maxwell to Photons

How did a minor flaw in our understanding of light spark the greatest scientific revolution of the 20th century? This interactive lecture bridges the gap between classical electromagnetism and the bizarre, fascinating world of quantum mechanics. 

For decades, classical physics successfully described light as a continuous, perfectly predictable electromagnetic wave. We will start by exploring this classical foundation, visualizing how changing electric and magnetic fields propagate through space. But classical physics had a fundamental limit: it assumed energy was always continuous. We will explore the paradigm shift that shattered this idea, introducing wave-particle duality and the realization that light actually exists as discrete, indivisible packets of energy called **photons**.

---

## Part 1: The Classical Foundation (Maxwell's Equations)
Light is a form of electromagnetic radiation. In classical electrodynamics, Maxwell's equations demonstrate that fluctuations in electric and magnetic fields propagate at a constant speed in a vacuum. 

*   **The Speed of Light:** Derived from the constants of a vacuum, the velocity is $$v=\frac{1}{\sqrt{\mu_0\epsilon_0}}$$, which calculates exactly to 299,792,458 m/s.
*   **Wave Properties:** These waves carry energy (intensity) and momentum (radiation pressure)[cite: 1].
*   **Polarization:** As transverse waves, light can be polarized, meaning its electric field oscillates in a specific geometric orientation[cite: 1].

### Simulation 1: EM Wave Propagation
Save this code as `em_wave.html` to run the real-time simulation:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Electromagnetic Wave Simulation</title>
    <style>
        body { font-family: sans-serif; background: #121212; color: #fff; display: flex; flex-direction: column; align-items: center; padding: 20px; }
        canvas { background: #000; border: 1px solid #333; border-radius: 8px; }
    </style>
</head>
<body>
    <h2>Real-Time EM Wave Propagation</h2>
    <canvas id="emCanvas" width="800" height="400"></canvas>
    <script>
        const canvas = document.getElementById('emCanvas');
        const ctx = canvas.getContext('2d');
        let time = 0;

        function animate() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            const centerY = canvas.height / 2;
            const k = (2 * Math.PI) / 150;
            const omega = 4 * 0.05; 

            ctx.beginPath(); ctx.moveTo(0, centerY); ctx.lineTo(canvas.width, centerY); ctx.strokeStyle = '#555'; ctx.stroke();

            let ePoints = [], bPoints = [];
            for (let x = 0; x < canvas.width; x += 15) {
                const waveVal = 120 * Math.sin(k * x - time * omega);
                const eY = centerY - waveVal;
                ePoints.push({x: x, y: eY});
                ctx.beginPath(); ctx.moveTo(x, centerY); ctx.lineTo(x, eY); ctx.strokeStyle = 'rgba(255, 68, 68, 0.7)'; ctx.stroke();

                const angle = Math.PI / 4; 
                const bX = x - waveVal * Math.cos(angle) * 0.4;
                const bY = centerY + waveVal * Math.sin(angle) * 0.4;
                bPoints.push({x: bX, y: bY});
                ctx.beginPath(); ctx.moveTo(x, centerY); ctx.lineTo(bX, bY); ctx.strokeStyle = 'rgba(68, 170, 255, 0.7)'; ctx.stroke();
            }
            time += 1; requestAnimationFrame(animate);
        }
        animate();
    </script>
</body>
</html>