const malla = {
  "Semestre 1": [
    "Formación ciudadana",
    "Taller de operaciones básicas de cocina",
    "Taller de panadería y bollería",
    "Higiene en la industria gastronómica",
    "Resolución de problemas en datos e información"
  ],
  "Semestre 2": [
    "Administración",
    "Taller de cocina internacional",
    "Taller de pastelería",
    "Nutrición y dietética",
    "Costos y presupuestos"
  ]
  // puedes seguir con los otros semestres
};

const container = document.getElementById("malla");

for (const [semestre, asignaturas] of Object.entries(malla)) {
  const box = document.createElement("div");
  box.className = "semestre";
  box.innerHTML = `<h2>${semestre}</h2>`;

  asignaturas.forEach(asig => {
    const id = `${semestre}-${asig}`;
    const saved = localStorage.getItem(id) === "true";

    const row = document.createElement("div");
    row.className = "asignatura";
    row.innerHTML = `
      <label>${asig}</label>
      <input type="checkbox" ${saved ? "checked" : ""} onchange="localStorage.setItem('${id}', this.checked)">
    `;
    box.appendChild(row);
  });

  container.appendChild(box);
}
