            // Cargar el script para computadoras
            
                const scale = 2;

                // LAZY HELPERS
                const $ = (el, scope = document) => scope.getElementById(el);

                // ELEMENTS
                const imagesGrid = $("imagesGrid");

                // TODO implement
                // ResizeObserver to determine aspectRatio => needed rows
                let aspectRatio = 0;
                const wrapper = $("wrapper");
                const myObserver = new ResizeObserver((entries) => {
                    entries.forEach((entry) => {
                        aspectRatio = entry.contentRect.height / entry.contentRect.width;
                        console.log({ aspectRatio });
                    });
                });

                myObserver.observe(wrapper);

                // UTILITIES
                const specificImages = [
                "https://github.com/ignack/imagen/blob/main/tattoo%20e1.jpeg?raw=true",
                "https://github.com/ignack/imagen/blob/main/tattooe2.jpeg?raw=truee",
                "https://github.com/ignack/imagen/blob/main/tattooe3.jpeg?raw=true",
                "https://github.com/ignack/imagen/blob/main/logo.jpeg?raw=true",
                "https://github.com/ignack/imagen/blob/main/tattoo%20e4.jpeg?raw=true",
                "https://github.com/ignack/imagen/blob/main/tattoo%20e5.jpeg?raw=true",
                "https://github.com/ignack/imagen/blob/main/tatuaje2.jpeg?raw=true",
                "https://github.com/ignack/imagen/blob/main/tatuaje3.jpeg?raw=true",
                "https://github.com/ignack/imagen/blob/main/tatuaje5.jpeg?raw=true",
                "https://github.com/ignack/imagen/blob/main/tatuaje6.jpeg?raw=true",
                "https://github.com/ignack/imagen/blob/main/tattoo2.jpeg?raw=true",
                "https://github.com/ignack/imagen/blob/main/tattoo3.jpeg?raw=true",
                "https://github.com/ignack/imagen/blob/main/tattoo4.jpeg?raw=true",
                // Agrega más rutas según sea necesario
                ];

const getSpecificImg = (index) => {
        const adjustedIndex = index % specificImages.length;
                return specificImages[adjustedIndex];
};

const camel2Kebab = (prop) =>
        prop.replace(/[A-Z]/g, (cap) => "-" + cap.toLowerCase());

const getNode = (tagName, options) => {
        const tagElement = document.createElementNS(
                "http://www.w3.org/2000/svg",
                tagName
                );

                for (const attribute in options) {
                    tagElement.setAttribute(
                        camel2Kebab(attribute),
                        options[attribute]
                    );
        }
                return tagElement;
};

                const imageTag = {
                    type: "image",
                options: {
                    href: "",
                opacity: 1,
                pointerEvents: "visible",
                preserveAspectRatio: "none",
                clipPath: "url(#hexa)",
        },
};

const createImage = (x, y, row) => {
                    let newSVG = getNode("image", imageTag.options);
                imagesGrid.appendChild(newSVG);

                newSVG.setAttribute("href", getSpecificImg(row));
                newSVG.setAttribute("width", "100");
                newSVG.setAttribute("height", "100");

                newSVG.setAttribute(
                "style",
                `transform:translate(${x}%,${y}%)`
                );
                newSVG.setAttribute("data-row", `row-${row}`);
};

                const svgViewBox = $("svgViewBox");

const changeViewBoxSize = (element, factor) => {
        const viewBox = element.getAttribute("viewBox");
                const [x, y, width, height] = viewBox.split(" ").map(parseFloat);

                const newWidth = width*scale ;
                const newHeight = height/scale;

                const newViewBox = `${x} ${y} ${newWidth} ${newHeight}`;
                element.setAttribute("viewBox", newViewBox);
};

                changeViewBoxSize(svgViewBox, scale);

                const createAGrid = (options = { }) => {
        const defaults = {
                    columns: 11 / scale,
                rows: 33 / scale,
                offsetX: 10 * scale,
                offsetY: 4.05 * scale,
        };

                const {columns, rows, offsetX, offsetY} = {
                    ...defaults,
            ...options,
        };

                for (let i = 0; i < columns; i++) {
            const x = i * offsetX;

                for (let j = 0; j < rows; j++) {
                const translateX =
                j % 2 === 0 ? x : x - offsetX / 2;
                const translateY = j * offsetY;

                const index = (i * scale) * rows + (j * scale);

                console.log(
                `Image at position (${i}, ${j}): ${getSpecificImg(
                    index
                )}`
                );
                createImage(translateX, translateY, index);
            }
        }
};

                createAGrid();
    
        
